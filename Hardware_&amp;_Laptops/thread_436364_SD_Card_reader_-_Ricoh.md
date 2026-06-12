---
title: "SD Card reader - Ricoh"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by evilmonkey on 2007-05-07
Hello,

I have an Asus Z91N with an inbuilt SD/MS card reader. I would really like to have it read my SD cards. I have looked all over and couldn't find anything. Below is the output of lspci:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
01:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
```

I have enabled mod tifm_sd and mod mmc_core. Can anyone point me in the right direction? I know people have succeeded in getting this to work. I'm running on (K)ubuntu Feisty. Thanks. :)

---

### Post by WhiteHorse on 2007-07-30
Here is what worked for me:
I have an MSI 1029, aka megabook, with a Ricoh RL5c476 II (rev ac)
I had to locate a module for it. I found these instructions and it worked:


Code:

sudo aptitude install subversion
svn co [https://sdricohcs.svn.sourceforge.net/svnroot/sdricohcs](https://sdricohcs.svn.sourceforge.net/svnroot/sdricohcs) sdricohcs
cd sdricohcs/sdricoh_cs/

Quote:
Originally Posted by EvilMonkey
-Open the sdricoh_cs.c file
-find the reference to protocol.h
-comment out all the if kernel_version stuff around it
-make sure that sd.h is not commented out
Here is what my file looked like after editing:
> /*#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,22)
#include <linux/mmc/protocol.h>
#else*/
#include <linux/mmc/sd.h>
/*#endif*/

Code:

make
sudo make install
sudo modprobe sdricoh_cs

It should work then, but not for me, but I think I'm the only one :\
__________________

---

### Post by TheSe7enthSin on 2007-07-30
I get this when I enter "sudo make install"

```
if test ! -d /lib/modules/2.6.20-16-generic/kernel/drivers/mmc ; then mkdir -p /lib/modules/2.6.20-16-generic/kernel/drivers/mmc ; fi
install -D -m 644 *.ko /lib/modules/2.6.20-16-generic/kernel/drivers/mmc
install: cannot stat `*.ko': No such file or directory
make: *** [install] Error 1
```

I will never get this damn reader to work =[
I have a Dell M140. This is the my output of the lspci:

```
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

I've searched the forums and seen almost every topic. Every suggestion I have read has failed.

---

### Post by TheSe7enthSin on 2007-08-06
bump

---

### Post by Circuit99 on 2007-08-06
What I use is 

Scandisk - Mobile Card Reader/Writer (SDDR-103-e10m) (ABOUT £10)

BASICALLY  - plug SD & SDHC memory card into MobileMate SD which then is plugged into usb port on system.



Maybe have a look at this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#USB](http://ubuntuguide.org/wiki/Ubuntu:Feisty#USB)


[http://ubuntuforums.org/showthread.php?t=361236&highlight=sd+card+reader](http://ubuntuforums.org/showthread.php?t=361236&highlight=sd+card+reader)


On the second link on 3rd page GeneWine mentions they have a working 
SD Card reader - Ricoh

Maybe they can help.


:popcorn:

---

### Post by dabl on 2007-08-06
I bought the world's cheapest USB SD card reader -- I think it was $29.00 USD.  It is called "Dazzle", and "just works" on Ubuntu and Kubuntu Feisty.  Plug it into the USB port, and then I can insert the SD card from my Leica camera, or my wife's Canon camera, and copy off the photos. :)

---

### Post by jalirious on 2008-01-27
Quid from poundland (sd ->usb reader). Liverpool. Works fine, redhat, dapper, gutsy, etc.

---

### Post by jalirious on 2008-01-27
Quid (~$2) from poundland (sd ->usb reader). Liverpool. Works fine, redhat, dapper, gutsy, etc.

:guitar:

---

