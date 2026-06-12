---
title: "Suspend to ram - problem"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by Cuppa-Chino on 2007-04-03
Hello,

I am very happy with my current ubuntu system 6.10 edgy but there is one thing I just cannot get to work however hard I try.

Suspend to ram.

This is my hardware:
* core 2 duo
* 1 gig ram
* 2 gig swap file
* via 880 chipset based mobo
* pci express nvidia 7900
* sata hd's 
* wireless card PCI ralink 
* tv card PCI
* sound blaster audigy 2 PCI

if I try and  go to SUSPEND or HIBERNATE the screen goes blank and then the process aborts every thing remains powered up the screen obviously has power, although it is black.

I have read that SUSPEND2 is supposed to help but I am reluctant to kernel compile as this will mean I have to repeat it eveytime I upgrade (also am not sure about it).

Please help me - if there is any info you need please ask

thank you 

PS the system has no problem going into Standby in windows so it is not a hardware problem

---

### Post by aysiu on 2007-04-03
What model laptop do you have?

Suspend may just not work for that model with Ubuntu.

An aside: suspend did not work for me on my Dell Inspiron 500m for Dapper or Edgy, but I recently upgraded to Feisty beta, and suspend just started working straightaway, with no extra tweaking.

---

### Post by Cuppa-Chino on 2007-04-03
its not a laptop but a desktop - more details on the components

asrock 775 dual motherboard bios 1.8

I have power management options acpid & apmd on in the service settings menu I am using nvidia driver 1.0-8776

thanks

---

### Post by ongbk619 on 2007-05-09
Hi,

I also have problems with Ubuntu suspend.  I have an ASRock Dual Sata 2 that won't suspend properly.  I'm running Ubuntu Feisty for the AMD 64 architecture.

**What happened?**
I tried to suspend my desktop and the machine shut off.  When i tried to turn it on there was power only going to the fans, the cpu?,  the cd and dvd roms and the ps2 ports for the mouse and the keyboard.  The USB ports had no power and I'm pretty sure the hard disks weren't spinning.  I tried rebooting several times and came across the same symptoms.

**What I did...**
I reset the CMOS and reconfigured the BIOS.  Rebooted the system and everything is working again =) *phew* thought I had to buy some new hardware.

**What should i do now?**
Do I need to report this as a bug?

- Ben

---

