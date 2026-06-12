---
title: "SDHC card recognition 13.04"
date: 2013-05-04
forum: Hardware
---

### Post by Kuki666 on 2013-05-04
Hello, I have a problem with recognition of my Sony SDHC class 10 (40MB/s) 16GB card on Ubuntu 13.04. It was al OK on the same laptop with 12.04, and there is also all OK on my wife's laptop with 12.04. The card is recognized when I put it to my GoPro and conect GoPro with USB cable. I also try to format the card when it is in GoPro, but nothing happens.
 
There I have no problem with another SanDisc 16GB SDHC class 6 (30MB/s) card, or another 4GB SDHC SanDisc Class 2 card...

Plaese, somebody???

 Robert

---

### Post by Kuki666 on 2013-05-06
???

---

### Post by kurt18947 on 2013-05-06
I've read SDHC cards - various brands but no Sony -  in 13.04 using the integral card reader on a Brother Multi-function device with no issues.  If you can read other brand cards,  perhaps Sony is being Sony.  In other words, doing things a bit differently than everyone else.

---

### Post by mswoon on 2013-05-09
Yesterday I was not able to mount my Sony 16GB Class 10 SDHC, and googled and found your article. Then I tried with a Wintex Class10 SDHC that I knew worked, and for some reason, it did not mount as well! So I applied the tried-and-true solution that Microsoft taught, i.e. reboot. And indeed it worked after the laptop rebooted. I use a HP though, and I think it runs 12.10 instead of 13.04. Still, sometimes it does not hurt to reboot.

---

### Post by bcharlessr on 2013-05-09
I had a problem on my Sony laptop when I upgraded to WIN 7 (dual booted with Ubuntu). It would not detect (I think they removed the drivers in 7) for the SD card reader. I kept getting the exclamation point in device manager. I've had problems with the Ubuntu install since upgrading from 11.04 to 12.04 (I think it was actually related to one of the kernel updates about the same time) with the ricoh drivers. I originally thought it was the ricoh web cam, but my webcam has always worked even now running 12.10. What I did find was that the sd card reader is also a ricoh device. After updating the Ricoh drivers in WIN 7 it fixed the problem. I'm wondering if that may be your (and my) problem with the card reader. I also think it is responsible for the boot error I've been getting regarding the "Could not acquire name on session bus" which started about the same time. I just put two and two together after reading this post and will start looking for solutions to the card reader. Let me know if you find anything first...

---

### Post by afz12 on 2013-05-09
For reference, I use SD cards in my HP dv6 notebook and also in a much older ACER 5920 without any difficulty. However I use ADATA SD cards at 4 GB to 30 GB, class 10. I agree with previous members that the SD brand you are using may be the problem. Alternatively your notebook may have poor SD card support. Perhaps a combination of two weaknesses could account for your problems. I have used Ubuntu 12.04, 12.10, 13.04 with no problems. Also Linux Mint Mate and Mint Cinnamon both work fine. The ACER5920 is dual boot with Windows XP and all SD cards work fine here also. When I use Virtualbox and run XP as a VM on Linux, the SD card is recognized as a shared folder and works fine. Unfortunately this does not solve the problem, but given the wide range of OS etc that work fine with ADATA SD cards, formatted in FAT, NTFS and/or Ext4, I suspect the brand of SD card you have is the probable cause. Can you buy/borrow another SD brand and try this. If this is a combination effect, then your current SD card could well work on one machine but be too flaky to work on another!

---

### Post by mswoon on 2013-05-15
Sigh. I upgraded to 13.04. So the Sony 16 GB Class 10 SD card will NOT mount. The Wintex card still worked fine. dmesg shows a number of "error -110 sending status command"

---

### Post by Jack Harper on 2013-05-15
8 GB and 16 GB SDHC cards work on my 13.04 but those SDHC cards can behave erratically,one 16 GB card stopped working in a certain phone,the person tried formatting with Windows 7 but still appeared as "dead",formatting it with HP USB Disk Tool made it working again,formatting it on Linux again and it was also working,but when formatted from phone and Windows 7 it didnt work,card was not recognized in the phone or in the computer.It seems those cards often get screwed up and need occassional formatting.If you have Windows format the card with HP USB Disk Tool (use full formatting not quick),or format it in Linux on your wife's computer and try again.

---

### Post by mswoon on 2013-05-15
I filed a bug report and someone asked me to test with a new release candidate kernel, which indeed fixed the problem. 

[https://bugs.launchpad.net/bugs/1180182](https://bugs.launchpad.net/bugs/1180182)

---

