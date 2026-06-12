---
title: "Boot Ubuntu from Personal Media Drive?"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by luis.da on 2009-05-06
Hello everybody, Just as title says,
I want to boot ubunto from my personal media drive
how TO?
my PMD has a filesystem in NTFS.
How i can install ubuntu?
I want to install ubuntu 9.04 64-bit, coz' both computers (home and work) are 64, and i want to have the same configurations in both pc's

P.S. sorry about bad english xD

---

### Post by EXCiD3 on 2009-05-06
Check this out [http://www.squidoo.com/ubuntu-usb](http://www.squidoo.com/ubuntu-usb)

---

### Post by mlentink on 2009-05-06
I don't think the OP wants a persistent Live-install, but a full install on a usb drive, which is equally feasible, especially with later versions. 
In short, the procedure would be:
- Download the LiveCD, or install cd
- Choose install
- at the partitioning section, choose the usb-drive (you might want to use the whole thing), do not install on the built-in drive
- at the point where the graphical installer sums up your installation parameters, there's a button 'Advanced'. Click this, to make sure you install GRUB on the usb-drive, rather than on the internal disk. This is important! 
- Let the installer do its song and dance
- at reboot time, make sure you select the usb-drive, not the internal drive

Have fun...


P.S.: I use this quite frequently

---

