---
title: "Tecra M7 Suspend/Hibernate in Hardy/Intrepid/Jaunty"
date: 2009-03-25
forum: Hardware
---

### Post by nightalon on 2009-03-25
Hey everyone,

As I use Ubuntu more and more, the fact that I cannot suspend or hibernate bugs me more and more.  This is true with both the "nv" and "nvidia-glx" drivers.  This has been the case with Hardy, Intrepid, and now the Jaunty Alpha 6.

When will this end?  I read about something in the ATA kernel driver not properly terminating, postponing suspend by 5 minutes, but for once I waited 5 minutes, and no dice.  Ctrl-Alt-Bkspc does nothing; ditto for all the F* keys.

Toshiba Tecra M7
2.0 Ghz C2D T7200
4 GB RAM
320 GB Hitachi 7200 RPM SATA drive
Intel Calistoga 965 chipset
Nvidia Quadro NVS 110M (PCI-E x16)

Ubuntu Jaunty Jackalope Alpha 6 x64

Thanks!

---

### Post by Baboontu on 2009-05-04
Can someone please answer the question. this bugs me too since day one with ubuntu (5.10). using nvidia geforce4 440.

---

### Post by ssm360 on 2009-05-13
yea know the feeling nightalon, been trying 2 google this hibernate prob still cant find a fix that works,


my system spec's are

AMD Athlon 64 X2 4600+
Asus M2N32-SLi-DLX nForce 590 SLi Mobo
2Gb Corsair DDR2 800Mhz XMS2-6400C4 TwinX
E-VGA NVIDIA GeForce 8800 GT 512Mb
Creative Sound Blaster X-Fi Xtreme Gamer


running Jaunty, im not sure but its starting 2 seem like this prob is just related 2 nvidia cards/drivers, but i use the 185.19 drivers from the website

---

### Post by errold32 on 2009-11-27
I am having this problem with 9.04, as well as 9.10 karmic on a tecra m7 x86 with a nvidia nv 110M

---

### Post by arpad.szasz on 2009-12-16
I had a similar problem: after initiating suspend/hibernate, my Tecra A10 laptop would get a blank screen, but the CPU fan was still active. I had to wait for about 5 minutes for the suspend/hibernate process to finish and shut down my laptop. I am using Karmic but i had the same problem in Jaunty.

After some googling i found that the slow suspend/hibernate problems were caused by the IDE driver. The solution was quite easy: i enabled the AHCI option in my laptop's BIOS and now suspend/hibernate works as expected. (Of course my Windows XP installation broke :P)

I hope this helps.

[Arpi]("http://arpi.plenum.ro")

---

### Post by nightalon on 2011-06-01
The M7 has the ICH-7M Southbridge, but AHCI cannot be enabled in the BIOS.  Therefore, I don't think it can be enabled at all.

---

