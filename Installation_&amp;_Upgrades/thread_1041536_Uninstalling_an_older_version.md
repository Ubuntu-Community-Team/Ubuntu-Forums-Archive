---
title: "Uninstalling an older version?"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by billytalent on 2009-01-16
Hey guys, where would i be without you :)

I installed today a copy of [Helix]("http://www.e-fense.com/helix/") (im a CSI) on my machine, thing is, its basically just ubuntu with a few Forensic programs on there. I feel like im waisting space. 

The install is showing up as an older version of ubuntu (8.04), my question is, how can i uninstall this particular install without removing linux all together and therefor claiming back my 11GB i initially gave it?

Cheers!

---

### Post by Pumalite on 2009-01-16
Use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by billytalent on 2009-01-16
> **Pumalite said:**
> Use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

Cheers man, 

but could you tell me what to do once live CD is running?

ta

---

### Post by Pumalite on 2009-01-17
Post a screenshot of Gparted with the drive in question.

---

### Post by billytalent on 2009-01-17
> **Pumalite said:**
> Post a screenshot of Gparted with the drive in question.

[http://i39.tinypic.com/2rcu06w.png](http://i39.tinypic.com/2rcu06w.png)

there you go man, i have literally being searching far and wide for a solution to this problem. The best one i found was to find a different distro i liked and manually overright helix altogether, dont know how that would turn out though. 

how difficult can it be, a simple removal of one operating system.

---

### Post by Pumalite on 2009-01-17
Which one you want to get rid of?

---

### Post by billytalent on 2009-01-17
> **Pumalite said:**
> Which one you want to get rid of?

The one thats highlighted :) and of course the linux swap for it.

---

### Post by billytalent on 2009-01-17
Could i not just delete the partition and edit grub?

---

### Post by Pumalite on 2009-01-17
The problem you face is that they are both inside of an extended partition; as is your new install I asume. I would erase the extended partition and everything on it. Then install again what you want.

---

### Post by billytalent on 2009-01-17
> **Pumalite said:**
> The problem you face is that they are both inside of an extended partition; as is your new install I asume. I would erase the extended partition and everything on it. Then install again what you want.

So correct me if i am wrong, i should log out of linux, into windows, delete the linux partitions which will create unallocated space right? and then install ubuntu again?

when i delete the partition, do i delete all the files on there?

so when i do the ubuntu re-install i should have 20+GB instead of 2 linux installs of 10gb each?

just checking!?

---

### Post by Pumalite on 2009-01-17
Use:
Use Gparted Live CD:
[http://sourceforge.net/project/showf...kage_id=271779](http://sourceforge.net/project/showf...kage_id=271779)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Erase all we said after you saved your data and then reinstall Ubuntu.

---

### Post by billytalent on 2009-01-17
> **Pumalite said:**
> Use:
Use Gparted Live CD:
[http://sourceforge.net/project/showf...kage_id=271779](http://sourceforge.net/project/showf...kage_id=271779)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Erase all we said after you saved your data and then reinstall Ubuntu.

I used gparted live Cd to delete the partitions, then couldnt get into windows because grub got messed up, luckily i had helix live CD, went in there and installed grub again pphewwww

Now i have my ubuntu install and windows, ill delete the linux partition now via windows which will turn it into allocated space, then reinstall linux :)

Thanx for yourr help mate,

---

### Post by Pumalite on 2009-01-17
That's O.K. too.

---

