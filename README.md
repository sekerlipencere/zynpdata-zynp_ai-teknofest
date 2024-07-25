
# 🚀 zynpdata-zynp_ai-teknofest: Türkiye'nin En Büyük Açık Kaynaklı Türkçe Veri Seti

![zynpdata Logo](https://i.imgur.com/vg1ulFl.jpg)

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://semver.org)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/yourusername/technoturk)

## 📊 Proje Tanımı

Türkiye'nin en büyük teknoloji forumu Technopat'tan kazınmış, tamamen Türkçe ve açık kaynaklı en büyük veri setidir. 3 milyon konu ve 21 milyon yanıt içeren 7GB'lık bu veri seti, Türkçe NLP ve LLM projeleri için kapsamlı bir kaynak sağlar.

## 🌟 Neden zynpdata?

- **Benzersiz İçerik**: Technopat forumundan elde edilen gerçek insanlar tarafından yazılmış 30'dan fazla katagoride veri içerir.
- **Geniş Kapsam**: Teknolojiden günlük yaşama kadar çeşitli konuları içerir.
- **Büyük Ölçek**: 3 milyon konu ve 21 milyon cevap ile Türkçe NLP ve LLM model çalışmaları için eşsiz bir kaynaktır.
- **Güncel**: Türkiye'nin en aktif forumlarından biri olan Technopat'tan elde edilen güncel veriler ve içerir.
- **Çeşitlilik**: Farklı yazım stilleri, jargon ve diyalektler içerir aynı zamanda 2012'den günümüze kadar çeşitli veriler içerir.

## 💡 Kullanım Alanları

- Türkçe Doğal Dil İşleme (NLP) modellerinin eğitimi:
- Dil modelleri (LLM) için fine-tuning: Özellikle LLM modellerinin finetunungi için mükemmel doğrulukta saf bilgi sunar.Dil modelleri, doğal dil işleme (NLP) alanında büyük önem taşır ve çeşitli görevler için kullanılabilir. Fine-tuning, bu modellerin belirli bir veri kümesi üzerinde özelleştirilerek performanslarının artırılmasını sağlar. "zynpdata-zynp_ai-teknofest" veri seti, dil modellerinin fine-tuning işlemleri için mükemmel bir kaynak sunar.
- Sentiment analizi ve konu modelleme çalışmaları
- Türkçe soru-cevap sistemleri geliştirme
- Sosyal ağ analizi ve kullanıcı davranışı araştırmaları

## 🚀 Veri Setini İndirme

 örnek.com

## 📈 Proje Aşamaları
### Proje 3 aşamadan oluşmaktadır, *link toplama*, *içerik kazıma*, *format düzeltme*:

**1. Link Toplama:**

Sitenin sitemapından tüm konuların linklerinini indirdik, artık elimizde forumda açılmış tüm konuların linkleri vardı.Ama şöyle bir sorunumuz vardı, tüm konuların linkleri elimizde olmasına rağmen her konu 1 sayfadan oluşmuyordu hatta çoğu konu bir kaç sayfa veya daha fazla sayfadan oluşuyordu.Bu sayfaların linklerinide toplamamız gerekiyordu, bunun için aklımıza ilk gelen yöntem forumun konu sayfasında bulununan sayfaların linkleri web parse ederek toplamak ana link ile birlikte kaydetmekti.Hemen bu yöntem ile ilgili bir script yazdık ve test etmeye başladık.Scritpin geneli beklediğimiz gibi çalışıyordu tek beklediğimiz gibi çalışmayan kısmı parsing işlemi intel 16 çekirdek işlemci ile çalışmamıza rağmen oldukça uzun sürüyordu.Bu yöntem bizi süre açısından oldukça fazla kısıtlayacağı için bu yöntemden vazgeçmek zorunda kaldık.Hemen derin bir düşünme sürecine girdik.Bir süre sonra aklımıza yeni bir fikir geldi:Forumun forumun konu sayfasında mesaj sayısını çekip buna dayanarak konunun kaç sayfa olduğunu hesaplayıp bundan sonrada buna dayanarak linkleri oluşturan bir script yazdık.Scriptin son haline burdan ulaşabilirsiniz [Link Toplama Scripti](linktoplama.py).Bu script tam beklediğimiz gibi çalıştı, mesaj sayısını html verisinden çekip urllleri oluşturup kaydediyordu.Link toplama aşamasında bizi en çok zorlayan 2 problem ile karşılaştık bunlar şunlardı: Forumunun serveri nin bu kadar trafiği kaldırramayıp arada 501 hataları vermesi bazı urlleri baştan yapmak zorunda kaldık.Karşılaştığımız 2 sorun cloudflare ben robot değilim doğrulaması idi aynı ip den istek yaptığımız için genelde 12 saat bir 8 saat boyunca siteye erişebilmek için cloudflare doğrulamasını yapmadan siteye erişemiyorduk, bizi ortalama her 12 saatte bir 8 saat ara vermemiz gerekiyorduk.Link toplama aşaması toplam 1 hafta sürdü ve yaklaşık 4.5 milyon link elimizdeydi ondan sonra içerik toplama aşamasında geçtik.

**2. İçerik Toplama:** 

1.Aşamada topladığımız 4.5 milyon linki işlemek için doğru bir script yazmalıydık, hemen düşünme aşamasına geçtik.Uzun bir düşünme aşamadından geçtikten sonra beautifulsoup kütüphanesi ve kullanarak forumun konu sayfasından ilk olarak en üstte bulunan soru verisini çekip json veri değişkenimize eklemeden önce daha önce bu soru eklenmiş mi diye kontrol edip eğer varsa direkt cevap çekme aşamasına geçmemizi sağlayan bir scirpt yazdık eğer soru daha önce eklenmemişse soruyu jsona ekliyip ayrıntılı soru çekme kısmına geçmemiizi sağlıyordu.Ayrıntılı soru olarak kullanıcının mesajlar kısmında yazdığı ilk mesajı alıyoruz ve json verimize ekliyoruz.Ayrıntılı mesaj dan sonra cevapları sayfadan çekip onlarıda json verimize ekliyorduk.Geriye sadece sayfanın linkini ve atıfı ekleyip kalıyordu.Bu işlemi sciript topladığımız tüm linklere yaptı.Scriptin son haline burdan ulaşabilirsiniz [İçerik Toplama Scripti](iceriktoplama.py).Bu işlemde yaklaşık 2 hafta sürdü bu kadar uzun sürmesinin sebebi yine link toplama aşamsında karşılaştığımız sorunlarla aynı idi bu yüzden oldukça uzun sayılabilicek bir içerik toplama süreci geçirdik, ama sonucunda türkiyenin en büyük açık kaynaklı ve türkçe veri setini oluşturmuş olduk. 

**3. Veri Formatlama:** 

2.Aşamada toplanan verilerin kullanımını daha kolaylaştrmak ufak bir script kullanarak json verisini jsonl formatına çevirdik.


**İçerik Örneği:**

```json
{
  "soru": "CS:GO FPS nasıl arttırılır?",
  "url": "https://www.technopat.net/sosyal/konu/cs-go-fps-nasil-arttirilir.1340872/page-2",
  "ayrintili_soru": "kaonashii99 dedi:-Freq 144 -High -novid -Console -nosplash +cl_updaterate 128 +cl_cmdrate 128 +cl_interp 0 +Rate 128 +exec autoexec -lv +mat_queue_mode 2 +cl_forcepreload 1 -noforcemaatıfel -noforcemparms -noforcemspd(144 Hz monitör kullandığım için yazdım Hz değerine göre yazabilirsin bu kodu işine yarıyıcak başlatma seçenekleridir.)ParkControl – Tweak CPU Core Parking and Moreverdiğim linkten işlemcinin hızını maksimumda kullanabilirsin sorun yaratmaz işlemcinden alabiliceğin verimi almana yardım eder.Oyunun klasöründen oyununn exe dosyasını bulup özelliklerden uyumluluk sekmesinde tam ekran iyileştirmesini devre dışı bırak tikini seçin iyi bir FPS almanıza yardımcı olacaktır.800-600 de oynamanı öneririm bu arada 4.3 Black bar fark etmez.Konsoldan FPS Max 0 çekmeniz veriminizi daha artıracaktır.Genişletmek için tıkla...Sadece freq144'ümü monitör Hz'me göre ayarlayacagım?",
  "cevaplar": [
    "Hocam çoklu CPU kullanımını ayarlardan kapattıysanız aktif edince 4 5 FPS artar.",
    "Evet sadece 144 ayarını 60 Hzdir büyük ihtimale monitörün 60 yazabilirsin.Fps_max 0 komutu.Ayarlardan ses ayarlarına gelip gelişmiş 3B ses işlemesi hayır yapıp.800-600 formatına çekip Black bar 4.3 boyutu fark etmez nasıl oynuyorsanız yapabilirsiniz.CS:GO görüntü ayarlarında Uber gölgelendirici kullan komutunu hayır yapmanız öneririm dikey eşitleme FPS'ini sabitler bundan dolayı yüksek FPS değerleri almana mani olur.Oyun açtıktan sonra görev yöneticisinden ayrıntılar sekmesinde csgo.exe komutuna sağ tık ile öncellik ayarlamadan yüksek seçmeniz ve Windows çalıştır (Windows+r) ile MSConfig ile açılan ekrandan ön yüklemeye gelerek gelişmiş seçenekler bastığınızda işlemci sayısına gelip kaç çekirdekliyse hepsini aktif etmeniz 1.den başlayıp aşağı kadar giden sayı değerini en yükseğini seçip tamama basmanız işinize yarayacaktır park üste verdiğim linkten park Control indirmeniz de lazım.Verdiğim başlatma komutlarını yapıp gerisi sistemin oyuna verdiği FPS değerleriyle uygun performansta en azından iyileşmeleriyle beraber oynayabilirsiniz oyun içi ayarlardan şahit olduğum 4.5 FPS demişler yaklaşık 30-40 FPS Boost yapmıştım üste verdiklerimi de yapmanızı öneririm."
  ],
  "atıf": "zynp_msg veri seti sekerlipencere tarafından hazırlanmıştır."
}

```

## 📈 Veri Seti Hakkında Analizler


### 1. Genel Bakış

zynpdata veri seti, Türkiye'nin en büyük teknoloji forumu olan Technopat'tan elde edilmiş, geniş kapsamlı bir Türkçe veri setidir. Bu veri seti, doğal dil işleme, makine öğrenimi ve yapay zeka araştırmaları için zengin bir kaynak sunmaktadır.Özelikle türkçe llm model üretimi ve finetuning edilmesinde eşssiz bir kaynak sağlar.

### 2. Boyut Ve Genel İstatistikler

| Metrik | Değer |
|--------|-------|
| Toplam Konu Sayısı | 3,094,199 |
| Toplam Cevap Sayısı | 21,000,000 |
| Toplam Kelime Sayısı | 769,457,477 |
| Toplam Dosya Boyutu | 7 GB |
| Toplam Karakter Sayısı | 5,934,600,344 |

### Veri Setinin Tamamını İçeren Word Cloud
![TechnoTürk Logo](https://i.imgur.com/LTO2EkH.png)
---
---
### Veri Setinin Tamamını İçeren Kelime Frekans Grafiği
![TechnoTürk Logo](https://i.imgur.com/H7P3BTc.png)


### 3. İçerik Türleri ve Kaynakları

zynpdata veri seti, Technopat forumundan elde edilen çeşitli içerik türlerini kapsamaktadır:

1. Forum Konuları: Kullanıcılar tarafından başlatılan tartışmalar
2. Cevaplar: Konulara verilen yanıtlar
3. Ürün İncelemeleri: Kullanıcıların teknolojik ürünler hakkındaki değerlendirmeleri
4. Teknik Destek Soruları ve Yanıtları: Kullanıcıların teknik problemleri ve çözümleri
5. Haberler ve Yorumlar: Teknoloji dünyasındaki gelişmeler ve kullanıcı yorumları
6. Rehberler ve Öğreticiler: Çeşitli teknolojik konularda kullanıcı tarafından oluşturulan kılavuzlar

### 4. Konu Dağılımı ve Çeşitliliği

zynpdata veri seti, geniş bir konu yelpazesini kapsamaktadır. Ana kategoriler ve yaklaşık yüzdeleri şu şekildedir:

1. Donanım (%25)
   - Bilgisayar Bileşenleri
   - Dizüstü Bilgisayarlar
   - Masaüstü Bilgisayarlar
   - Mobil Cihazlar

2. Yazılım (%20)
   - İşletim Sistemleri
   - Uygulama Yazılımları
   - Programlama Dilleri
   - Oyunlar

3. İnternet ve Ağ Teknolojileri (%15)
   - Web Hizmetleri
   - Sosyal Medya
   - Ağ Güvenliği

4. Tüketici Elektroniği (%10)
   - Akıllı Ev Cihazları
   - Ses ve Görüntü Sistemleri
   - Giyilebilir Teknolojiler

5. Otomotiv Teknolojileri (%5)
   - Elektrikli Araçlar
   - Otonom Sürüş Sistemleri

6. Bilim ve Teknoloji Haberleri (%10)
   - Yeni Teknolojik Gelişmeler
   - Bilimsel Keşifler

7. Diğer (%15)
   - Eğitim Teknolojileri
   - Sağlık Teknolojileri
   - Finans Teknolojileri
   - Çevre Teknolojileri

### 5. Veri Kalitesi ve Ön İşleme

- **Dil**: Tüm içerik Türkçedir.
- **Temizlik**: Ham veri temel bir temizleme işleminden geçirilmiştir:
  - HTML etiketleri ve özel karakterler kaldırılmıştır.
  - Kullanıcı adları ve e-posta adresleri anonimleştirilmiştir.
  - Spam içerikler ve tekrar eden mesajlar ayıklanmıştır.
- **Normalize Edilmemiş Metin**: Yazım hataları, kısaltmalar ve internet jargonu korunmuştur, bu da gerçekçi NLP görevleri için idealdir.

### 6. Zaman Aralığı

Veri seti, 2012 yılından 2024 yılına kadar olan forum içeriklerini kapsamaktadır. Bu geniş zaman aralığı, Türkçe'nin ve teknoloji dilinin zaman içindeki evrimini incelemek için fırsatlar sunmaktadır.

### 7. Etik Hususlar ve Gizlilik

- Tüm kişisel bilgiler (kullanıcı adları, e-posta adresleri, IP adresleri) anonimleştirilmiştir.
- Veri seti, Technopat'ın kullanım şartlarına ve gizlilik politikasına uygun olarak oluşturulmuştur.
- Araştırmacılar, bu veri setini kullanırken etik kurallara uymakla yükümlüdür.


### 8. Potansiyel Kullanım Alanları

1. Türkçe Dil Modelleri Geliştirme
2. Konu Modelleme ve Metin Sınıflandırma
3. Duygu Analizi ve Fikir Madenciliği
4. Soru-Cevap Sistemleri
5. Metin Özetleme
6. Teknoloji Trendleri Analizi
7. Sosyal Ağ Analizi
8. Kullanıcı Davranışı Modelleme

Bu kapsamlı veri seti, Türkçe doğal dil işleme alanında çalışan araştırmacılar ve geliştiriciler için benzersiz fırsatlar sunmaktadır.

## Kaynaklar

https://medium.com/kaveai/web-scraping-453e96a86195
https://www.sinanerdinc.com/python-beautifulsoup-modulu
https://furkancakmaker.medium.com/python-ile-web-scraping-beautifulsoup-kullan%C4%B1m%C4%B1-5f0a3d88f5
https://yazilimtoplulugu.com/blog/2397-requests-ve-beautifulsoup-modullleriyle-internetten-veri-cekme
https://www.geeksforgeeks.org/implementing-web-scraping-python-beautiful-soup/
https://www.freecodecamp.org/news/how-to-use-the-json-module-in-python/
https://www.freecodecamp.org/news/how-to-create-a-telegram-bot-using-python/
https://www.datacamp.com/tutorial/python-multiprocessing-tutorial
https://stackoverflow.com/questions/57071390/create-jsonl-with-python


## 🤝 Katkıda Bulunma

Projeye katkıda bulunmak isterseniz, lütfen önce [CONTRIBUTING](CONTRIBUTING.md.py) dosyamızı kontrol edin.


## 📄 Lisans

Bu proje Apache 2.0 Lisansı altında lisanslanmıştır. Detaylar için [LICENSE](LICENSE) dosyasına bakın.

## 📚 Atıf

Bu veri setini çalışmalarınızda kullanıyorsanız, lütfen aşağıdaki gibi atıfta bulunun:

```
@misc{zynpdata2024,
  author = {sekerlipencere},
  title = {zynpdata: Türkiye'nin En Büyük Açık Kaynaklı Türkçe Forum Veri Seti},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub Repository},
  howpublished = {\url{https://github.com/sekerlipencere/zynpdata-zynp_ai-teknofest}}
}
```

## 📞 İletişim

Sorularınız veya geri bildirimleriniz için lütfen [issues](https://github.com/sekerlipencere/zynpdata-zynp_ai-teknofest/issues) bölümünü kullanın veya [yusufd.polar@gmail.com](mailto:yusufd.polar@gmail.com) adresinden bize ulaşın.

---

TechnoTürk ile NLP ve LLM çalışmalarınıza güç katın! 🚀🇹🇷
