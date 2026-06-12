---
title: "Ubuntu 9.04 recognizes SATA Master, but not PATA slave"
date: 2009-05-28
forum: Hardware
---

### Post by Rhemat on 2009-05-28
I currently have a 40GB SATA drive set as master in my machine, and I have a 80GB PATA slave drive in there.  I was once able to configure a 40GB PATA as master with the 80GB PATA as slave (before that 40GB PATA died), but now it no longer detects the PATA.  I have the PATA plugged into the slave part of the cable, set to cable select, with the master end just dangling.  I had tried taking the jumper off (since there is no slave setting listed on the drive), and plugging it into the master end, but the result is the same.  Both drives are detected in BIOS, but only the SATA is recognized by Ubuntu 9.04.
Let me know if you need any other information, or if you have any suggestions.  Thanks in advance.

---

### Post by munky99999 on 2009-05-28
Sata is always master. IDE hardrives still need a master even if your sata is your primary drive.

Set the jumper on ur IDE drive to master. That should fix your problem.

---

### Post by lindsay7 on 2009-05-28
+1 with munky.  Single IDE drives need to be at the end of the flat cable. Set it as the master. Sata drives do not care about slave and master settings.

---

### Post by Rhemat on 2009-05-29
Thanks munky99999, that solved the problem.  I also configured fstab to automount it on boot by doing:

/dev/sdb1       /home/[user name here]/Storage     ext3     defaults     0     0

---

