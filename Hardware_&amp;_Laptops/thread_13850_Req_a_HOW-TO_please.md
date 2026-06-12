---
title: "Req a HOW-TO please"
date: 2005-02-03
forum: Hardware &amp; Laptops
---

### Post by ctt1wbw on 2005-02-03
Can some put up a HOW-TO about making a separate partition for your /home folder?

I've got room in my XP partition to make another 10 gig Linux partition.  I would like to know how to make a separate /home mount with that extra 10 gigs.  :)

Thanks in advance!

---

### Post by AlBundy on 2005-02-03
I think when you installing UBUNTU you can create custom partiton, then you can choose /home mounting point.

---

### Post by Davo on 2005-02-03
[QUOTE=AlBundy]I think when you installing UBUNTU you can create custom partiton, then you can choose /home mounting point.[/QUOTE]

Indeed you can, you can choose its purpose (I can't remember the exact word) so just set it to /home :)

---

### Post by wulf on 2005-02-03
[QUOTE=Davo]Indeed you can, you can choose its purpose (I can't remember the exact word) so just set it to /home :)[/QUOTE]
 I've not done it, but I think you can also do it post install. I imagine the procedure is to add the new disk, partition it as you wish and format the the target partition with a suitable filesystem. Then, I think, you'd mount it, copy your existing home directory across (including all the settings) and then edit /etc/fstab to point to the new disk. I'm not sure about the final details of switching though. Another option would be to mount the new disk as a subdirectory of your home folder, for example /home/username/store.

Have a dig around - I'm sure these things are covered in existing HowTo documents and aren't particularly Ubuntu specific.

Wulf

---

### Post by Rancoras on 2005-02-03
The HOWTO forum is not the place to request howtos.  The correct place is the appropriate support forum,

---

### Post by piedamaro on 2005-02-03
I have a separate home partition. Copy (or move) your home dir to the new partition, then in /etc/fstab add something like: 
/dev/hda2               /home                   ext3    defaults    0 0

cross your fingers and reboot :D

---

### Post by ctt1wbw on 2005-02-03
[QUOTE=piedamaro]I have a separate home partition. Copy (or move) your home dir to the new partition, then in /etc/fstab add something like: 
/dev/hda2               /home                   ext3    defaults    0 0

cross your fingers and reboot :D[/QUOTE]


Okay, thanks.  I'm going to try to start making a new partition now...

---

### Post by ctt1wbw on 2005-02-04
Bad idea.  Something happened to my hard drive and I had to wipe it CLEAN.  I have no Ubuntu now.  I will install it later.  Im in XP for now...  :oops:

---

