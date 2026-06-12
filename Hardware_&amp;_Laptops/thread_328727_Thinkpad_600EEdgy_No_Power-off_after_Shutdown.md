---
title: "Thinkpad 600E/Edgy: No Power-off after Shutdown"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by fiestaforever on 2006-12-31
Hi, 
a newly installed Xubuntu 6.10 Edgy (kernel 2.6.17-10 generic) on an old Thinkpad 600E (PII-366) won't power off after shutdown, but sit at the boot/shutdown image with the bar graph obviously "finished" (can't see it go down, but seem to indicate "done"). 
Another machine I have (Lifebook S-4542 w/ PIII-600) will power off fine. 
What I've seen from other threads, those problems are not all that rare, but there doesn't seem to be a clear picture. 
Probably some issue with ACPI? 
Could anyone give me some directions how to handle that? 

(OTOH there seem to be issues with overheating when using/forcing ACPI, so I'm a little worried to use it, esp. in Edgy.)

---

### Post by jruschme on 2006-12-31
I don't have Ubuntu on my 600E at the moment, but I seem to recall that you do need to force ACPI to have the automatic shutdown work. (There should be a way with APM, but it's well below my depth.)

IIRC, you want 'acpi=force pci=noacpi' in the boot options.

---

### Post by fiestaforever on 2006-12-31
jruschme, I understand that you have some distro with ACPI on your 600E. 
With which kernel, and dou you have problems with overheating? 
And what would the "pci=noacpi" part be good for?

---

### Post by le_jawa on 2006-12-31
Fiestaforever,

Since Ubuntu didn't recognize a recent ACPI controller on your system at startup, it probably didn't install any ACPI or power management packages.  From what I've learned in my experience in setting up an old CLI server, here are the packages that I can tell you to install:

acpi
acpid
acpi-support
gnome-power-manager
powermanagement-interface
powermgmt-base
powernowd

The powernow daemon is what (if I understand you correctly) you need, but the rest is needed to support and manage it.  powernow is responsible for throttling the CPU to help conserve power and reduce heat usage on processors that support these features (AMD processors with PowerNow! and Intel processors from the Pentium M and forward, as well as any TransMeta Crueso (sp?) processor).

I know that installing most of these packages got my shutdown to work correctly, but I'm still struggling with getting my server to sleep.  I suspect that simply installing these packages will get your system going with the right kernel parameters.

About those parameters.  Definitely include acpi=force, unless you have a P4 processor with hyperthreading; in which case acpi=ht may be your best bet.  pci=noacpi will turn off IRQ routing through acpi, as well as all ACPI PCI management (say that three times fast! ;-) ).  acpi=noirq will accomplish about the same thing it looks like.  Also, look at your processes and see if apm is running.  If it is, apm=off should be included, as APM and ACPI can't run together, according to what I've read.  Also, after you boot, run dmesg and look for errors about the APIC.  If there are any, include the argument lapic, which will allow Linux to turn on the APIC even if BIOS has it turned off.

Basically, you kernel line in menu.lst should look something like this, depending on your OS, hardware and requirements:
```

kernel          /vmlinuz-2.6.17-10-server root=/dev/mapper/Ubuntu-root ro splash  acpi=force apm=off lapic

```One final note:  all of this assumes that you are using 32-bit Ubuntu 6.10 (Edgy Eft) with GNOME.  If your configuration is different, you may have to adjust some of this.

Good luck and let us know  how it goes!  What you learn may help me; who knows!

:D

Jason

---

### Post by boiboi on 2007-01-01
Hi fiestaforever, I almost intalled Ubunto on my 600E, but I'll wait for your post. I also have a T21, but I don't think it would make any difference. What wireless or ethernet card are you planning to use, by the way?

Found this: 
[http://www.mueller.ch.vu/misc/tp600e_en.html](http://www.mueller.ch.vu/misc/tp600e_en.html)

---

### Post by fiestaforever on 2007-01-01
boiboi, 

I'm sorry that I can't help you much because I won't finish the installation on this Thinkpad. 

It was actually only a testing ground for another machine, a TP 390E that has essentially the same hardware and that I'll get to install next week (but I won't have much time for it, so I wanted to practice with this one first). 

Concerning the shutdown, 'acpi=force pci=noacpi' did the trick for me. Wireless is not working, and I have no idea how to get that going. I actually had it working with Vector some time ago but can't remember how I did that (it required some manual adjustment). 
The link you posted is a nice find, although I disagree with the wifi part: I remember that I had both proper shutdown (which requires ACPI) and working wifi. Right now I only have a wired IBM PCMCIA NIC (that has, BTW, been working since the install of Xubuntu without any additional effort). 

I never cared for the modem, and my 600E has one very special oddity, which I've experienced for years: 
There is no sound coming out of the speakers in **any** operating sytem **except** Win 2000/XP (I've tried Win 98, OS/2, BeOS and two flavors of Linux, nothing works) **regardless** of drivers. I can hear the sound over headphones if the drivers are working, but never over the speakers. There seems to be something that mysteriously mutes the speakers and thats somehow overridden in WinNT-based OSs. Could never find it out, and it doesn't matter anymore. Since I know that this is a lost cause, I didn't try to install sound drivers this time. 

For myself, I'm going to switch to a "much newer" 600X in the next weeks. 

BTW: The video drivers for this card are really crappy and only usable in 16Bit-mode.

---

