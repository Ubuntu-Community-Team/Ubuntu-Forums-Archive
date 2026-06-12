---
title: "[SOLVED] ITX hardware help"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2006-11-02
I need a little help on hardware. I am currently thinking of building a ITX PC that's gonna carry Ubuntu 6.10 as OS. Se below what i need.

* USB boot support (I want the OS to boot from USB)
* minimum of 1Gb RAM (preferbly 2Gb support).
* minimum of 1024x768 resolution
* 10/100/1000 Network
* 1 PCI slot
* a processor that makes Ubuntu 6.10 run ok.

Anyone know a ITX motherboard that fits this spec and works with latest Ubuntu? :-k

---

### Post by Jaxilian on 2006-11-07
bump

---

### Post by Jaxilian on 2006-11-17
bump

---

### Post by Jaxilian on 2007-07-02
bump, same but with Ubuntu 7.04

---

### Post by BillDozer on 2007-07-02
Hi Flodis,

I made myself a MythTV box with a VIA EPIA EX1500G motherboard. Look at my [thread]("http://ubuntuforums.org/showthread.php?t=478229"). It does not start from USB though, just from an ordinary harddisk. I am not sure, but I think you can also start from USB, I'll check it when I get near my PC again.

---

### Post by Jaxilian on 2007-07-02
> **BillDozer said:**
> Hi Flodis,

I made myself a MythTV box with a VIA EPIA EX1500G motherboard. Look at my [thread]("http://ubuntuforums.org/showthread.php?t=478229"). It does not start from USB though, just from an ordinary harddisk. I am not sure, but I think you can also start from USB, I'll check it when I get near my PC again.

Thanks. I appreciate it very much. The USB boot is the vital part.

---

### Post by BillDozer on 2007-07-02
I just booted the machine and looked in the BIOS. There you could choose between a large number of boot devices, 3 of them were USB related, so this should not be a problem. But I think most modern motherboards have USB boot possibilities.

---

### Post by jamb on 2007-07-11
Hi flodis,
I just bought some ITX stuff, but I have not yet received all parts to start to play with it.
VIA EPIA MII 12000G: 
- 1GB DIMM, 
- C3-prcessor (1.2 GHz), 
- 100 Mbps LAN, 
- Built-in DVD-decoder, 
- 5.1 surround sound.
- UniChrome graphics 
My priorities selecting this VIA board have been Linux compatibility, and to balance power consumption and performance. I intend to boot from CF, and eliminating the HDD. IDE to CF adapters should plug directly into the 40-pin connector on your board.

---

### Post by Jaxilian on 2007-07-11
> **jamb said:**
> Hi flodis,
I just bought some ITX stuff, but I have not yet received all parts to start to play with it.
VIA EPIA MII 12000G: 
- 1GB DIMM, 
- C3-prcessor (1.2 GHz), 
- 100 Mbps LAN, 
- Built-in DVD-decoder, 
- 5.1 surround sound.
- UniChrome graphics 
My priorities selecting this VIA board have been Linux compatibility, and to balance power consumption and performance. I intend to boot from CF, and eliminating the HDD. IDE to CF adapters should plug directly into the 40-pin connector on your board.

ok cool, let me know how it goes :guitar:

---

### Post by jamb on 2007-07-12
Hi flodis,
Just learned some about CF and adapters. They are as evil as all other HW. Make sure they support DMA...A linux vote for Sandisk and Kingston (one CF/4GB-U is on the way to me). 
Here are two links about CF and IDE-CF adapters which I have found informative,
[http://www.kingston.com/flash/cf_ultimate.asp]("http://www.kingston.com/flash/cf_ultimate.asp")
[http://www.acscontrol.com/index_ACS.asp]("http://www.acscontrol.com/index_ACS.asp")

---

