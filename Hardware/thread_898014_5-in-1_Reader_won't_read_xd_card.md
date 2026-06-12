---
title: "5-in-1 Reader won't read xd card"
date: 2008-08-22
forum: Hardware
---

### Post by Edgeman16 on 2008-08-22
Hello,

I have an Acer Aspire 5670 laptop running ubuntu gutsy.
It has a Texas Instruments 5-in-1 card reader on the front that supports xd memory cards.
However I have been unsuccessful in my efforts to use it for any of my xd cards.
I attempted to search the forums but everything was regarding SD cards. I have loaded the following via modprobe just in case:
```
tifm_7xx1
tifm_core
tifm_sd
```
Upon plugging in the memory card the following appear in /var/log/messages:

```
Aug 22 19:48:02 edgetop kernel: [ 2789.988000] tifm_core: SmartMedia/xD card detected in socket 0:0
Aug 22 19:48:08 edgetop kernel: [ 2795.688000] tifm0 : demand removing card from socket 0:0
```

Here's the (possibly?) related lines from lspci:
```
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Thanks in advance

---

### Post by macvr on 2008-09-03
xD card is still in Early stages of development: check this links[http://ubuntuforums.org/showpost.php?p=4039759&postcount=13]("http://ubuntuforums.org/showpost.php?p=4039759&postcount=13")

to keep track check this site: [http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver]("http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver")

i too hav an xD card ,its recognized only in windows 
 keeping my fingers crossed to delete my Windows Xp partition soon

---

### Post by DougR55 on 2009-11-28
> **macvr said:**
> xD card is still in Early stages of development: check this links[http://ubuntuforums.org/showpost.php?p=4039759&postcount=13](http://ubuntuforums.org/showpost.php?p=4039759&postcount=13)

to keep track check this site: [http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver](http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver)

i too hav an xD card ,its recognized only in windows 
 keeping my fingers crossed to delete my Windows Xp partition soon


My xD memory card reader on my Dell Inspiron E1505 wont read in Linux. . only in Winxp. Any help???

---

