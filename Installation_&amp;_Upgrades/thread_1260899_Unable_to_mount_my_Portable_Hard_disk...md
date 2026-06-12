---
title: "Unable to mount my Portable Hard disk.."
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by aprashanth on 2009-09-08
I have a Segate Hard Disk 320 Gb.. All of a sudden I am not able to mount it to any  machine.. please help me...

---

### Post by zipperback on 2009-09-08
If you are unable to mount the hard drive on any computer then it is probably a hardware problem.

Do you hear the drive spin up when it is turned on?
Did you check the cables that are connected to the hard drive?
Was the hard drive part of a raid array?
How old is the drive?
Did it recently make any strange noises?
Are you properly unmounting the drive before removing it from your computer?
If the drive is a USB drive, please connect the drive to your computer and then tell us the output of the following command:

```

lsusb

```

- zipperback
:popcorn:

---

### Post by aprashanth on 2009-09-08
Sorry for the delayed response as my system got struck and.. bla bla bla...


I can feel the drive rotating.. but there is no any sound or any thing like that.. 
It did give a beep sound the moment when I put the drive in a Old windows P3 machine..The drive is pretty new.. its not even 3 months old...

the output for the command is..
Bus 001 Device 005: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 004: ID 0bc2:2100 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:0317 Hewlett-Packard LaserJet 1200
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by aprashanth on 2009-09-08
Thanks for your help.. I was able to figure out that it is problem with the Portable Disk..

---

### Post by zipperback on 2009-09-09
I'm curious. Could you please tell me what the problem turned out to be?

Thanks,

- zipperback
:popcorn:

---

