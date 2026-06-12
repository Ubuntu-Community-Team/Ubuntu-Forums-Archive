---
title: "Card reader in notebook not working"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Armor on 2007-03-11
I have a Gateway M320 (1.5ghz Celeron, 768 RAM), Edgy version of Ubuntu. Can't get the SD card reader to work. I've tried following this guide [http://www.ubuntuforums.org/showthread.php?t=315497](http://www.ubuntuforums.org/showthread.php?t=315497) , but since there is no "Mass Storage Controller" or whatever output, it won't work. Any ideas? Here is lspci output:


> leigh-mobile@leigh-mobile:~$ lspci
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
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
leigh-mobile@leigh-mobile:~$ 


---

### Post by huami on 2007-03-14
Hi, I have the same problem on my gateway notebook, I don't know how to mount SD card.
some info from lspci:
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)

I have kernel 2.6.17-11-generic, ubuntu 6.10
and some info from dmesg
[17181829.584000] pccard: PCMCIA card inserted into slot 0
[17181829.584000] cs: memory probe 0xe0200000-0xe02fffff: excluding 0xe0200000-0xe020ffff
[17181829.584000] pcmcia: registering new device pcmcia0.0

how to mount sd card?

---

### Post by ender42 on 2007-03-14
Had the same issue, posted about it awhile back.  No real responses.  There are some things you can try for diagnostic listed toward the end of page one (unix geek friend of mine tried diagnosing the issue...)

[http://ubuntuforums.org/showthread.php?t=347585](http://ubuntuforums.org/showthread.php?t=347585)

The work-around I'm using is a Warty Live CD, to gain access to it.  It appears the longer-term solution is to use an older version of Ubuntu. :)

---

### Post by treesurf on 2007-03-15
This link has some directions for getting the Ricoh card readers to work.

[http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working](http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working)

---

### Post by dptxp on 2007-03-17
MY ENE card reader is not detected.

---

### Post by albanetcsr on 2007-07-29
I have Gateway M320X laptop with Ricoh Co Ltd RL5c476 II (rev a9). Just installed Feisty 7.04, everything seems to work except SD card reader.

Here is lspci output:
> 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Here is what dmesg says when I remove and insert the card (no other references):
> 
[  147.420000] pccard: card ejected from slot 0
[  152.404000] pccard: PCMCIA card inserted into slot 0
[  152.404000] pcmcia: registering new device pcmcia0.0


As suggested here: [http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working](http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working) , I tried adding **tifm_sd** to /etc/modules but to no avail. However, adapter model mentioned there is different.

I also tried adding **tifm_7xx1**and **tifm_core** to modules (with no result), though I don't quite understand how TI drivers can be used on Ricoh controller at all, unless it's a clone.

I did a couple of hours of googling on this and I think I tried everything I found.
Any help will be appreciated.

---

### Post by sa87 on 2007-09-14
FWIW, I hope you got this sorted, I have the same reader model as you (running Fiesty) and the instructions in the following post got things working!

[http://ubuntuforums.org/showpost.php?p=2671230&postcount=3](http://ubuntuforums.org/showpost.php?p=2671230&postcount=3)

To clarify the second section (editing the sdricoh_cs.c file) I did the following:
```

gedit sdricoh_cs.c

```
find the section that contains "protocol.h" (using ctrl+f)
add comment's ( /* & */)around the whole "if...endif" statement
copy the whole line "#include <linux/mmc/sd.h>" immediately after the commented section.

below is what I now have inside the sdricoh_cs.c file before I then continued with the third section of Dixon's run-through
(but this may be different depending on the version of the source you checked out from cvs)
```

#include <linux/mmc/host.h>
#include <linux/mmc/mmc.h>
/* #if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,22)
#include <linux/mmc/protocol.h>
#else
#include <linux/mmc/sd.h>
#endif*/
#include <linux/mmc/sd.h>
```

---

