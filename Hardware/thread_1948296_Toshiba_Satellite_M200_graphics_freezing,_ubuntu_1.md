---
title: "Toshiba Satellite M200 graphics freezing, ubuntu 10.04"
date: 2012-03-28
forum: Hardware
---

### Post by ezrvinh on 2012-03-28
Hello friendly people of the ubuntu forums,

My laptop is glitching out on me and I can't pin down why. I'm worried it might be a hardware issue so I'll explain what's happening and hope someone out there knows what's going wrong.

I just got an error screen (first time) **before** the bios screen came up. It said something about CMOS but I stupidly didn't read it and just pressed f1 for "load default settings".

My computer started to freeze a couple of weeks ago at fairly random intervals. Usually the screen goes black, sometimes there is a grey square on it, sometimes the colors get mixed up and there are lines like it has suddenly been converted into 16 or 8 bit color for those pixels. Also the little light that means that the hard drive is spinning comes on and stays on until I switch the laptop off (the hard drive is actually spinning, I can hear/feel it).
The most common time for this to happen is when I boot or when I resume after suspending my laptop. Sometimes it happens for no reason whatsoever.

The laptop is around 5 years old but I love it, it's my first ubuntu computer, I dual boot with windows 7 but very rarely use it. I've already done a complete reinstall of ubuntu 10.04 but that didn't fix it.

I have started trying to program video games using code-blocks and get a lot of segmentation faults, could that have caused it? It might be that my laptop is incompatible with the newer updates of ubuntu (#40). Any insights are appreciated!

 - ezrvinh

---

### Post by UltimateCat on 2012-03-28
Our members will need more information to assist you.
```
lspci

```Is a command for displaying info about all PCI buses in your system and all devices connected to them.  Useful when you want to diagnose problems or report bugs related to PCI devices.

Do you know what on board graphics you have?  Chipset?

Is your processor AMD or Intel or other?

Digging deep into the details of a particular graphics card ; determining what type of memory a particular card uses is difficult.

I strongly urge you to be careful with the BIO's or you could have a crash-
This website can assist you with a driver and info.

[http://manpages.ubuntu.com/manpages/lucid/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/radeon.4.html)

[http://ubuntu.com/community](http://ubuntu.com/community)

[http://www.ubuntu.com/certification/make/Toshiba/](http://www.ubuntu.com/certification/make/Toshiba/)

---

### Post by ezrvinh on 2012-03-28
Thanks for the quick reply :3
I have an intel 1.7 ghz dual core processor and the chipset is the 945GM 

I don't have anything constantly plugged in, just the laptop by itself.

Okay, here are the results of 
```
lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller



Something I forgot to mention earlier is that when I restart the computer after a crash my networking is always disabled. That could be a clue...

---

