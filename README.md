# chillington_dplearning_hw
 
The aim of this project is to develop a system that classifies SMS or email messages as "spam" (unsolicited) or "ham" (normal) using machine learning and deep learning methods. The project follows a typical data science workflow, including data cleaning, feature extraction, modeling, and evaluation.

Imp Notes: python version: 3.12.2
Required libraries can be installed using
pip install -r requirements.txt 

Train: 3618
Val:   775
Test:  776


ROLE 1 emir
Data Preparation and Preprocessing
Dataset:
The spam.csv dataset is included in the project and loaded using the Pandas library.
Cleaning:
Unnecessary columns were removed, missing values (null) were checked, and duplicate records were cleaned.
Label Encoding:
Text labels were converted into numerical format:
ham → 0
spam → 1
Data Splitting:
The dataset was divided into:
70% training
15% validation
15% test

Feature Extraction (Vectorization)
To convert text data into a numerical format understandable by machines, the TF-IDF (Term Frequency–Inverse Document Frequency) method was used.
The top 5000 features (terms) were selected to construct the feature vectors.

Role 2 Melih 
Baseline Model
Logistic Regression:
A Logistic Regression model was trained using the scikit-learn library.
Performance Evaluation:
The model was evaluated using:
Accuracy
Precision
Recall
F1-score
Additionally, a Confusion Matrix was used to analyze classification errors.


Deep Learning Model (PyTorch)
Model Architecture (MLP – Multilayer Perceptron):
Input Layer: 5000 units (TF-IDF features)
Hidden Layers:
256 units (Linear + ReLU)
128 units (Linear + ReLU)
Output Layer: 1 neuron (logit output)
Training:
Loss Function: BCEWithLogitsLoss
Optimizer: Adam
Epochs: 20
During training, both training loss and validation loss were tracked and visualized.

ROLE 3 – Zeynep
Model Improvement and Regularization
The goal is to:
Prevent overfitting
Improve generalization
Make training more efficient
This ensures the model not only detects known spam but is also robust against unseen spam patterns.

Techniques Applied
Batch Normalization: Stabilizes training and accelerates convergence
Dropout: Reduces overfitting by randomly disabling neurons
Early Stopping: Stops training when validation performance stops improving
Regularization (L1/L2): Penalizes large weights to improve generalization
Model Architecture Improvements: Enhances learning capacity and stability
Hyperparameter Optimization: Improves model performance through tuning

Forward Function (Updated Flow)
The forward pass is structured as follows:
Linear Layer (fc1)
Batch Normalization (bn1)
Activation (ReLU)
Dropout
Linear Layer (fc2)
Batch Normalization (bn2)
Activation (ReLU)
Dropout
Output Layer (fc3)


ROLE 4 – Jale
Hyperparameter Optimization and Optimization Algorithms
Adam vs SGD:
In this project, both Stochastic Gradient Descent (SGD) and Adam optimizers were used.
SGD is a simple and classical optimization method that updates model parameters using gradients. However, it may converge slowly and requires careful tuning of the learning rate.
Adam adapts the learning rate for each parameter using moment estimates, leading to faster and more stable convergence.
While Adam generally performs better in terms of speed and stability, SGD can sometimes provide better generalization.

Additional Techniques
He (Kaiming) Initialization:
Since ReLU activation is used, weights were initialized using He Initialization to compensate for variance loss caused by zeroing negative values.
Layer Normalization:
In NLP tasks, input sequences may vary in length, and Batch Normalization may not perform well with small batch sizes. Therefore, Layer Normalization was used to address the internal covariate shift problem, making it more suitable for text data.
Adam vs SGD Experiment:
An experiment was conducted to compare Adam and SGD, showing that Adam converges faster and more stably than classical SGD.








----------
Bu projenin amacı, SMS veya e-posta mesajlarını "spam" (istenmeyen) veya "ham" (normal) olarak sınıflandırmak için makine öğrenmesi ve derin öğrenme yöntemlerini kullanan bir sistem geliştirmektir. Proje, tipik bir veri bilimi iş akışını (veri temizleme, özellik çıkarma, modelleme ve değerlendirme) takip etmektedir.

Imp Notes: python version: 3.12.2
gereken kütüphaneleri
pip install -r requirements.txt 
komutu ile kurabilirsiniz


Train: 3618
Val:   775
Test:  776


ROLE 1 emir

Veri Hazırlığı ve Ön İşleme
Veri Seti: 

spam.csv veri seti projeye dahil edilmiş ve Pandas kütüphanesi ile yüklenmiştir.
Temizlik: Gereksiz sütunlar kaldırılmış, eksik değerler (null) kontrol edilmiş ve yinelenen veriler (duplicates) temizlenmiştir.
Etiketleme: Metin etiketleri sayısal değerlere dönüştürülmüştür (ham -> 0, spam -> 1).
Veri Bölme: Veri seti, modelin doğruluğunu test etmek amacıyla %70 eğitim, %15 doğrulama ve %15 test seti olarak ayrılmıştır.

Özellik Çıkarımı (Vectorization)
Metin verilerini bilgisayarın anlayabileceği sayısal formata getirmek için TF-IDF (Term Frequency-Inverse Document Frequency) yöntemi kullanılmıştır. En önemli 5000 özellik (kelime öbeği) seçilerek vektör matrisleri oluşturulmuştur.

ROLE 2 melih

Baseline (Temel) Model Çalışması
Logistic Regression: İlk aşamada scikit-learn kütüphanesi kullanılarak bir Lojistik Regresyon modeli eğitilmiştir.
Performans: Model; Accuracy (Doğruluk), Precision (Kesinlik), Recall (Duyarlılık) ve F1 skoru gibi metriklerle değerlendirilmiş ve Karmaşıklık Matrisi (Confusion Matrix) üzerinden hataları analiz edilmiştir.

Derin Öğrenme Modeli (PyTorch)
Model Mimarisi: PyTorch kütüphanesi kullanılarak bir MLP (Multilayer Perceptron - Çok Katmanlı Algılayıcı) modeli tasarlanmıştır:
Giriş Katmanı: 5000 birim (TF-IDF özellikleri).
Gizli Katmanlar: 256 ve 128 birimlik iki tam bağlantılı (linear) katman ve ReLU aktivasyon fonksiyonları.
Çıkış Katmanı: Tek bir nöron (Logit).
Eğitim: Model, BCEWithLogitsLoss kayıp fonksiyonu ve Adam optimizasyon algoritması ile 20 dönem (epoch) boyunca eğitilmiştir. Eğitim süreci boyunca hem eğitim hem de doğrulama kayıpları (loss) takip edilerek görselleştirilmiştir.


ROLE 3 zeynep
Mevcut modelin eğitim verisine aşırı uyum sağlamasını (overfitting) engellemeyi, genelleme yeteneğini artırmayı ve eğitim sürecini verimli hale getirmeyi amaçlar.
Bu şekilde, modelin sadece spam tespit etmesini değil, aynı zamanda yeni ve daha önce görülmemiş spam türlerine karşı da dayanıklı (robust) olmasını sağlayacaktır.

Batch Normalization:
Dropout:
Early Stopping:
Regularization (L1/L2):
Model Mimarisi İyileştirmeleri:
Hiperparametre Optimizasyonu:

--
forward Fonksiyonu:
Akış şu şekilde güncellenecek:
Doğrusal Katman (fc1)
Batch Norm 1 (bn1)
Aktivasyon (ReLU)
Dropout (dropout)
Doğrusal Katman (fc2)
Batch Norm 2 (bn2)
Aktivasyon (ReLU)
Dropout (dropout)
Çıkış Katmanı (fc3)

Role 4 Jale
Hyperparameter and optimization
Adam Optimizer vs SGD 

He (Kaiming) Initialization: Since we use ReLU activation in our network, we initialized weights with He Initialization to compensate for variance loss caused by zeroing negative values[cite: 94, 95].
Layer Normalization: In NLP projects, data can have variable lengths and Batch Norm can fail on single-sample batches, so we solved the Internal Covariate Shift problem using Layer Normalization, the gold standard for text data[cite: 118, 128].
Adam vs SGD Comparison: We added an experiment showing how industry-standard Adam (Momentum + RMSProp)[cite: 114, 115] converges faster and more stably than classic SGD.

In this project, Stochastic Gradient Descent (SGD) and Adam optimizers were used. SGD is a simple and classical optimization method that updates model parameters using gradients, but it may converge slowly and requires careful tuning of the learning rate. In contrast, Adam adapts the learning rate for each parameter using moment estimates, resulting in faster and more stable convergence. While Adam generally performs better in terms of speed, SGD can sometimes provide better generalization.
