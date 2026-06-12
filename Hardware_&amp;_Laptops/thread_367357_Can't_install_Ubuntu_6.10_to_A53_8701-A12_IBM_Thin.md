---
title: "Can't install Ubuntu 6.10 to A53 8701-A12 IBM ThinkCentre PC"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by azat_aja_donk on 2007-02-22
I have A53 8701 IBM ThinkCentre. I want to install Ubuntu 6.10 Desktop to that PC. I can't intall it, because the device disk is ot detected at step 5 of 6 on installation progress. I updated PC's BIOS, and i tried to install again but i get fail to install it. Can anyone help me? 
Tq

---

### Post by aberry5555 on 2007-02-22
is your hard-drive sata or pata?

---

### Post by azat_aja_donk on 2007-02-22
My Harddrive is SATA. 
FYI.
I have another PC with SATA too with detail spec:
- Intel P4 2.66GHz Dual Core FSB533Mhz
- Intel D101GGCL Chipset (Sound, VGA, LAN)
- Visipro 512MB x 2 PC3200 DDR2 (1GB total)
- Seagate Barracuda 120GB PC7200 SATA
- VGA Radeon X300SE PCIE Hyper Memory
- DVD Combo 
- Casing Simbadda Micro ATX
- Keyboard Logitect + Mouse Optical Scroll Logitech
- Monitor Benq 15"LCD FP531G Silver black 12ms Response Time

I installed ubuntu 6.10, No problem and it's running fine. 
What's wrong about this ?

---

### Post by aberry5555 on 2007-02-23
could you give me more detailed specs on the pc you're trying to install to?

---

### Post by azat_aja_donk on 2007-02-23
Ok, this is detail of my PC's spec: 

IBM ThinkCenter A53, 8701-A12
Intel Pentium 4 Processor 541-3,2Ghz HT Tech
Integrated Chipset SiS 662
512MB RAM PC4200
80GB 7200RPM SATA
PCI/AGP Tower (4x4)
48x CD-ROM, Gigabit Ethernet
4 USB 2.0 (back), Parallel, RJ-45, Serial
2 USB 2.0 (front), Keyboard (PS/2), Mouse
Headphone/Line Out, External Microphone
External Display, 3,5” 1.44MB
15” IBM CRT Monitor

---

### Post by aberry5555 on 2007-02-23
I think the reason for this is that it hasn't got the drivers for your sis chipset, here's the link for the linux drivers:

[http://www.sis.com/download/download_step1.php](http://www.sis.com/download/download_step1.php)

you will have to choose the options yourself as theirs no direct link to it, then follow the read me on how to install it. hopefully once this is installed you will be able to see your sata hard-drives

good luck!

---

### Post by azat_aja_donk on 2007-02-24
I tried to go to sis webpages and look the driver for SIS Chipset that Linux platform but there is nothink for Kernel 2.6.17

IBM ThinkCentre A53 8701-A12 is not compatible and not ready to Linux, but ready to MS Windows Vista. Good job IBM....!!

---

### Post by aberry5555 on 2007-02-25
no no, the kernel 2.6.10 driver is compatble beyond 2.6.10, it should be OK I think, give it a try.

---

### Post by ~takumi~ on 2007-03-21
I have the same problem here, not only that, but the sound will not work either on live-CD.

The easiest sulution would probably be to buy a new sound card and HD without S-ATA.

I though IBM/Lenivo should be pretty compitable with Linux...

I've tried several distros, all having the same problem.

---

