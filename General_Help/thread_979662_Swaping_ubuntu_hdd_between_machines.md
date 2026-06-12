---
title: "Swaping ubuntu hdd between machines"
date: 2008-11-12
forum: General Help
---

### Post by antmenj on 2008-11-12
I swaped a dapper install hard drive from an AMD i386 machine to a pentium unit and hardy hdd the other way and both hdds booted and ran in the other machine.  Is that normal or a fluke?

This would never work on windoz without identical hardware or lots of new drivers.

Whats going on?  I thought when installing ubuntu to hdd the install compiled specialy for the hardware found.  Is that right:??

Rather than downloading hours of updates for a new install can I just clone a  drive with gparted and stick it in another machine?  I'v cloned a few before to go in the same machine but not others machines:-k

---

### Post by Zimmer on 2008-11-12
At a rough guess, you should be ok installing as the primary drive.

The problems you 'could' face are with fstab, GRUB, and xorg.conf.

fstab  since it will hold details of the UUID of the drives connected ,
GRUB you will probably have loaded to the MBR of the drive so it will expect the cloned drive to be the primary drive in the new install.

X, hmmm, well Hardy and Intrepid will attempt autodetection of graphic cards monitors etc so depending on what you did to your original install (loading proprietry 3D drivers for a specific card for example  you could run into problems (hiccups) with screen res etc.

It is a question of learning and experimentation. The more it fails, the more you learn. This should lead us both to investigate properly what happens at boot!

The Joy of Linux ... log files that tell you what went wrong...

EDIT  !!
Dapper X does not work the same as Hardy and Intrepid, so more care with the xorg.conf

---

### Post by Zimmer on 2008-11-12
As for the Windows not coping with a similar situation I have to disappoint you. I swapped a drive from an old AMD duron tower to an Intel Pentium Biostar with little difficulty barring the dreaded Windows registering the software routine! oh, and I had to install Video drivers, but I equate that to messing with the 3D drivers and xorg...

---

