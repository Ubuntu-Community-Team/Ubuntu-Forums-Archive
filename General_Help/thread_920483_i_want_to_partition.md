---
title: "i want to partition"
date: 2008-09-15
forum: General Help
---

### Post by douggiephresh on 2008-09-15
I want to install windows xp alongside ubuntu hardy (i just cant get games to work on ubuntu). Do i have to partition part of my drive or can I just try to install windows?

---

### Post by ThrobbingBrain66 on 2008-09-15
> **douggiephresh said:**
> I want to install windows xp alongside ubuntu hardy (i just cant get games to work on ubuntu). Do i have to partition part of my drive or can I just try to install windows?

I would grab a Gparted Live CD, partition my drive with that and then install Windows.  Windows XP doesn't have a built-in partitioner in the setup like Vista does.  Even if it did, I don't know that I'd trust it.  Gparted rocks.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by douggiephresh on 2008-09-15
I have gparted live, but i dont know how to partition with it. where can i find an instructional?

---

### Post by Elfy on 2008-09-15
The information available at both gparted and partedmagic (similar) is quite good - there are screenshots there as well. The programs are quite intuitive once you start - if you move from left to right on the screen that's what the epartition editor is going to do. Whatever you do make sure you have backups of anything you can't afford to lose.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

There is some also here [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) - not specific to gparted as such.

Not sure whether any of them say that it can possibly take hours to finish depending on what you are doing.

Did I say make sure you have backups...

---

### Post by douggiephresh on 2008-09-15
how can i make a backup of my current setup?

---

### Post by douggiephresh on 2008-09-15
Ok, i read the directions and im stuck at step one. When i select the drive i want to partition, it doesnt give me the option to resize/move.

---

### Post by bodhi.zazen on 2008-09-15
> **douggiephresh said:**
> Ok, i read the directions and im stuck at step one. When i select the drive i want to partition, it doesnt give me the option to resize/move.

My guess : You can not resize a mounted partition. Use a live CD and unmount the partition.

---

### Post by Sef on 2008-09-15
> Ok, i read the directions and im stuck at step one. When i select the drive i want to partition, it doesnt give me the option to resize/move.


1) Does it give you any options?  

2) Is the drive mounted or unmounted? (Running or not running.)

---

