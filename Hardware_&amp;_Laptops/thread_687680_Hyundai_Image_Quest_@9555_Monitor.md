---
title: "Hyundai Image Quest @9555 Monitor"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by neset on 2008-02-04
[ ImageQuest Q995 ]

    Monitor Properties:
      Monitor Name                                      ImageQuest Q995
      Monitor ID                                      IQT2995
      Model                                             Q995
      Monitor Type                                  19" CRT
      Product Date                                   Week 38 / 2004
      Ser&#351;al Number                                 143820040916
      Max. Screen Dimensions                 35 cm x 26 cm (17.2")
      Heigt:Weight                                  4:3
      Horizontal Freq                                30 - 96 kHz
      Vertical Freq                                     50 - 150 Hz
      Max. Resolution                              1600 x 1200
      Gama                                              2.20
      DPMS Mode Support                         Standby, Suspend, Active-Off

     Supported Display Modes:
      640 x 480                                         150 Hz
      800 x 600                                         150 Hz
      1024 x 768                                        115 Hz
      1152 x 864                                        105 Hz
      1280 x 768                                        115 Hz
      1280 x 800                                        110 Hz
      1280 x 1024                                       85 Hz
      1366 x 768                                        115 Hz
      1400 x 1050                                       85 Hz
      1440 x 900                                        100 Hz
      1600 x 1200                                       75 Hz

//////////////////////////////////////////////////////////

 [ ImageQuest Q995 ]

    Monitör Özellikleri:
      Monitör Ad&#305;                                       ImageQuest Q995
      Monitör Kimli&#287;i                                   IQT2995
      Model                                             Q995
      Monitör Türü                                      19" CRT
      Üretim Tarihi                                     Hafta 38 / 2004
      Seri Numaras&#305;                                     143820040916
      En Büyük Görünür Ekran Boyutu                     35 cm x 26 cm (17.2")
      Resim En-Boy Oran&#305;                                4:3
      Yatay Frekans                                     30 - 96 kHz
      Dikey Frekans                                     50 - 150 Hz
      En Yüksek Çözünürlük                              1600 x 1200
      Gama                                              2.20
      DPMS Mod Deste&#287;i                                  Standby, Suspend, Active-Off

    Desteklenen Görüntü Modlar&#305;:
      640 x 480                                         150 Hz
      800 x 600                                         150 Hz
      1024 x 768                                        115 Hz
      1152 x 864                                        105 Hz
      1280 x 768                                        115 Hz
      1280 x 800                                        110 Hz
      1280 x 1024                                       85 Hz
      1366 x 768                                        115 Hz
      1400 x 1050                                       85 Hz
      1440 x 900                                        100 Hz
      1600 x 1200                                       75 Hz

//////////////////////////////
I installed Ubuntu 7.10 x64 on my PC. X window did not start properly. that I try different monitor. (Samsung 793 DF). then everything went normal. All graphic system worked. 

How can I find my monitor Driver. (Hyundai Image Quest Q9995 19")

thanks.
////////////////////////////////
Bilgisayar&#305;ma Ubuntu 7.10 linux kurdum. X window aç&#305;l&#305;&#351;&#305;nda bütün ekran birbirine geçmi&#351; gibi kay&#305;k görüntü geldi. Her &#351;ey belirsizle&#351;ti. Daha sonra Samsung 793 DF monitör ba&#287;lad&#305;&#287;&#305;mda her hangi bir de&#287;i&#351;iklik yapmadan bütün grafik özellikleri aktif hale geldi. 

Hyundai Image Quest Q995 Monitörüne ait sürücüyü nereden bulabilirim. 

&#351;imdiden te&#351;ekkür ederim.

---

### Post by taurus on 2008-02-04
What happens if you remove the Samsung and hook up the Hyundai.  Then, boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by neset on 2008-02-07
thank you I try it but it did not worked. Monitor closing than opening itself then all screen stay black.

---

