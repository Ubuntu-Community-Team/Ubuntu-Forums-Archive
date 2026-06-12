---
title: "[SOLVED] Performance problem with Compaq laptop"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by javi0084 on 2007-12-17
Hi, everyone. I am fairly new to Ubuntu and thankfully I've been able to find all the solutions on the forums without having to start many new threads.

I bought a Compaq Presario F730US last night and installed the latest version of Ubuntu, I did played around with Vista before I installed Ubuntu and noticed that Vista is a lot faster on my laptop. It takes almost a minute for any window to open in Ubuntu and about 10 seconds to switch between tabs. In order to install it, I had to press F6 and type noapic then press enter. I don't know if this would affect the performance at all but its probably worth noting. The specs are:

Microprocessor   	1.8 GHz AMD Athlon 64 X2 Dual-Core Mobile Technology TK-55
Microprocessor Cache   	512 KB L2 cache
Memory   	1024 MB DDR2 System Memory (2 Dimm)
Video Graphics   	NVIDIA GeForce Go 6100 (UMA)
Video Memory   	Up to 288 MB
Hard Drive   	120 GB (5400 RPM) Hard Drive (SATA)

Ubuntu 7.10 runs like a dream on my older desktop so I know theres a problem with the setup on my laptop. Also, when I was installing it, I just let it partition the drive itself.

Any suggestions are appreciated, thanks!

---

### Post by naja on 2007-12-17
hi
try installing nvidia-driver from restricted drivers manager.
be sure that you made a swap partiton.

---

### Post by javi0084 on 2007-12-18
I installed the NVIDIA and Broadcom drivers and that made no difference. As for the swap partition, I let Ubuntu take care of that stuff so I'm sure it created one.

I did noticed one difference on my laptop and desktop. I believe I went to Hardware Devices screen from one of the drop down menus (I can't access my computers right now so I can't look) and for the laptop it listed the hard drive under SCSI control and on the desktop it listed under IDE control. I really doubt my laptop has a SCSI drive so how would I change this? I can post screen shots later tonight if needed.

Thanks!

---

### Post by naja on 2007-12-18
hi
if u meant that changing tabs in Firefox is not so snappy as in windows,its the same here but it does only take less than a second to switch tabs.
Choose your Ubuntu at grub, press e then go to ur Kernel parameters (2nd line i think) e again and remove noapic.if it works better.edit /boot/grub/menu.list and und remove noapic from ur Kernel parameters to make it permanently.
i hope it will help,though i am not sure

---

### Post by javi0084 on 2007-12-19
Thanks so much for your help, its a lot faster now. I removed the noapic like you said.

---

### Post by naja on 2007-12-19
it was my pleasure
EDIT: Change the thread statue to SOLVED please

---

