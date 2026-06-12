---
title: "New to Ubuntu"
date: 2008-10-13
forum: General Help
---

### Post by cno on 2008-10-13
Hi. I'm really rather new to the whole linux environment and so far I'm not sure how I like it. I recognize how much more efficient it can be when everything works but at the moment I have several problems which I'm unable to fix. 

Instead of posting in every sub-forum for each of my problems I was thinking that perhaps its okay to do it here with the most important ones first. If this is wrong I'm sorry.

First of all my wireless is not working at all,

Secondly I can't get the mic to work, not the internal or external.

Also everything feels a bit slow.

I wrote lspci -nn and got this

laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP65 Memory Controller [10de:0444] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP65 LPC Bridge [10de:0442] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation MCP65 SMBus [10de:0446] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP65 SMU [10de:0447] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0454] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0455] (rev a3)
00:06.0 Ethernet controller [0200]: nVidia Corporation MCP65 Ethernet [10de:0450] (rev a3)
00:07.0 Audio device [0403]: nVidia Corporation MCP65 High Definition Audio [10de:044a] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI bridge [10de:0449] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP65 IDE [10de:0448] (rev a1)
00:0a.0 IDE interface [0101]: nVidia Corporation MCP65 SATA Controller [10de:045d] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation Device [10de:045b] (rev a1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:045a] (rev a1)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0458] (rev a1)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0459] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
05:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

My computer is a Hp Pavillion dv9500 and I use the 8.10 beta (could this be the cause to my problem?).

I really would like Ubuntu to work as it's supposed to because I'm sure that in perfect working order it would be preferable to Vista (which I hate). At the moment I'm dual-booting.

---

### Post by Sam on 2008-10-13
> **cno said:**
> First of all my wireless is not working at all

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

> **cno said:**
> Secondly I can't get the mic to work, not the internal or external

Double-clic on the speaker icon in the notification area and check that the mic is not muted.

> **cno said:**
> Also everything feels a bit slow.

Which cpu and how many memory do you have ? Did you enable the nvidia driver in "System / Administration / Hardware Drivers" ? Is there any process that eats the cpu when you run```
top
``` in a terminal ?

---

### Post by cno on 2008-10-13
Double-clic on the speaker icon in the notification area and check that the mic is not muted.



Which cpu and how many memory do you have ? Did you enable the nvidia driver in "System / Administration / Hardware Drivers" ? Is there any process that eats the cpu when you run```
top
``` in a terminal ?[/QUOTE]

Neither the nvidia driver or the broadcom driver could be activated it seemed through the hardware drivers program (or whatever it is).

Cpu is fine and almost uneaten;)

I have an Amd64 with two gb memory

Thanks for the help btw

---

### Post by cno on 2008-10-13
Actually now I could install the drivers and the wireless is working fine. Thanks. 

Don't know if the nvidia driver install did a lot of good but I was able to install it.

Now the main problem I have is to get skype to work, but I think that will have to wait untill tomorrow. I live in Sweden and now it's past midnight and work is early. If anybody knows about skype I would be grateful anyway.

See you later
Cno

---

### Post by seancarlgrech on 2008-10-13
this should help

[http://www.skype.com/intl/en/download/skype/linux/]("http://www.skype.com/intl/en/download/skype/linux/")

welcome to ubuntu :)

---

### Post by cno on 2008-10-13
> **seancarlgrech said:**
> this should help

[http://www.skype.com/intl/en/download/skype/linux/]("http://www.skype.com/intl/en/download/skype/linux/")

welcome to ubuntu :)

Thanks, I was really rather stupid before when I missed entering skypes options. Everything is fine and probably was always, just had to change a few settings.:lolflag: 

Now all my troubles are gone and I realize so far Ubuntu :guitar:

Thanks again.

---

