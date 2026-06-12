---
title: "Dell Inspiron 2500"
date: 2008-08-04
forum: General Help
---

### Post by emobrad on 2008-08-04
I recently acquired one of these notebooks, and I need some help installing the hardware drivers. There's a few major problems that need fixing.

1) The fans never work after I turn on the laptop. I'll turn it on, and the fans will rotate for a few seconds while the Bios screen is up, and then they shut off and never turn back on. I'm really paranoid that one of these days my computer will just completely melt and I will be out a laptop (even though it was free, it's nice to not have to sit at my desktop all the time)

2) I need to know what kind of video card I have, and if anyone knows where I can get the driver for it, so I can have a normal screen size. At the moment, half my windows think my screen is bigger than it is, and I can't fix it at all. (I'm running fluxbox by the way because my computer can't handle anything else to be quite honest)

3) I need to know how to install the wireless driver for it. It has an ethernet port, but I know it has wireless because the person who had it before obviously used wireless on it. Not to mention that it's a laptop and no company would honestly build a laptop without a wireless card... That would just be an inconveniance lol.

Those are the issues I pose to you my dear Ubuntu Forum members, please take pity on me and my crappy hardware to fix this problem lol.

Thanks in advance,
Brad

---

### Post by emobrad on 2008-08-04
Bump for needing help

---

### Post by adult swim on 2008-08-04
for you fans post 7 here should work
[http://ubuntuforums.org/showthread.php?t=733355](http://ubuntuforums.org/showthread.php?t=733355)

for your other problems lets get some information.
go to a terminal and type in ```
lspci
``` and paste your results here

---

### Post by emobrad on 2008-08-04
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
01:03.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:03.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:0b.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
02:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
02:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)

---

### Post by emobrad on 2008-08-04
bmup

---

### Post by emobrad on 2008-08-11
both compys died, bump again 'cus this still isn't fixed :(

---

