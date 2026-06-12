---
title: "Canon MG2520"
date: 2017-01-23
forum: Hardware
---

### Post by theozzlives2 on 2017-01-23
In the printer setup, it has MG2500 but I can't print a test page. I have a Pixima MG2520 and it don't seem supported. I checked Canon's site and they have no drivers for Linux. In the past, I've found Ubuntu to be very Canon friendly. So what's up?

---

### Post by theozzlives2 on 2017-01-23
OOPS! I found the correct setting. Never-mind!

---

### Post by QIII on 2017-01-23
Hello!

Could you share what that was in case someone else would benefit from the information, please?

Thanks!

---

### Post by pdc on 2017-01-23
In the Canon series of printers, the MG2520 would be in the MG2500 series; so the printer driver would be for the 2500 series ....... it might be the 2510 in one country, the 2520 in Australia, and the 2570 in Singapore ....... same driver works

Yes, Canon make 3 types of printer driver for this series of printer: they were issued in 2013: there is an rpm package, a debian package (that would work on ubuntu), and a source code package

get the debian package from here if anyone needs it [http://support-asia.canon-asia.com/contents/ASIA/EN/0100550201.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550201.html) and click to download [COLOR="#0000FF"]cnijfilter-mg2500series-4.00-1-deb.tar.gz[/COLOR]

terminal instructions (assuming saved into Downloads folder) are:
cd Downloads
tar -zxvf cnijfilter-mg2500series-4.00-1-deb.tar.gz
cd cnijfilter-mg2500series-4.00-1-deb
sudo ./install.sh

_______

for the scanner, Canon supply ScanGearMP: get it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100551901.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100551901.html) and download [COLOR="#0000FF"]scangearmp-mg2500series-2.20-1-deb.tar.gz[/COLOR] and install is in the same style as above: 

importantly, run the scanner with > [COLOR="#FF0000"]**scangearmp**[/COLOR] from the terminal till you set up a shortcut

---

### Post by theozzlives2 on 2017-01-24
Its in the list of printers. You just need to scroll down to the pixima printers.

---

