---
title: "Installer Hanging"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by Stewarty on 2009-04-08
Hi, im pretty new to all of this so please bear with me :P

okay, I'm trying to install Ubuntu on my laptop, an Advent 9315, but the installer hangs on the loading screen (ubuntu logo with an orange bar that fills underneath). I've run the "check disk for problems" utility and it hangs at the same section as an attempted install but if I use the disk in another PC the disk is able to load fine and run a Live Preview without any problems.

Can I assume this means a hardware incompatability? and what might be the best action to get it going?

Thanks :)

---

### Post by Stewarty on 2009-04-08
Okay, making progress :)

I've managed to get it to load as a live CD and even into the installer by setting acpi = off, noapic and nolapic under "Other Options" (F6)

My problem now is that once the installer gets to the partitioner it can read the hard drive fine but is unable to change any of the partition sizes.  I should mention that Vista is also installed on the hard drive and I am unable to delete it, I still require windows :(.  If I load a drive partitioner in Windows and create a new empty, unformated partition from theyre should I be able to use it to install Ubuntu?

---

### Post by upchucky on 2009-04-08
defrag windows, then defrag windows, then download gparted bootable cd to create the needed partitions.

create 10 gig partition for ubuntu, 1 gig swap partition, then rest of drive for ubuntu home partition.

get supergrub to help set up grub to dual boot win and ubuntu.

Advanced Supergrub

Get Supergrub to set up/repair Grub here:

[http://www.cyberciti.biz/tips/super-...inux-boot.html](http://www.cyberciti.biz/tips/super-...inux-boot.html)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

---

