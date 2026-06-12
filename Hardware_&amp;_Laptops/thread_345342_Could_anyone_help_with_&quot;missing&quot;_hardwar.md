---
title: "Could anyone help with &quot;missing&quot; hardware?"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by madsravn on 2007-01-24
Hey. I have a Zepto Znote 6615WD and I'm running Ubuntu Edgy Eft. I have webcam, special launcher buttons and memory card slots in my laptop, which doesn't work. I just did a lspci in terminal and here is output: 
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0398 (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
09:06.0 CardBus bridge: Texas Instruments Unknown device 8039
09:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
09:06.2 Mass storage controller: Texas Instruments Unknown device 803b
09:06.3 Class 0805: Texas Instruments Unknown device 803c

```

** Just noticed that something is wrong with something nVidia as well (it says "unknown" to it).

I'm new to linux, so hope you can and will help me...

 - Mads Ravn

---

### Post by renzokuken on 2007-01-24
i think the nvidia thing means that you havent got the nvidia drivers installed, although not essential, you get a massive grafix performance boost if you do.

do you know what grafix card/chipset your pc has?

---

### Post by madsravn on 2007-01-24
I have a  nVidia® Geforce Go 7600 512MB . I just think I installed the drivers... hmm... But thanks for the quick reply

---

### Post by renzokuken on 2007-01-24
search the forums for "envy" a brilliant script that does the installation for you. i think automatix does it too

---

### Post by madsravn on 2007-01-24
Thanks a lot. Will do. But anyone know anything about the other hardware? :)

---

