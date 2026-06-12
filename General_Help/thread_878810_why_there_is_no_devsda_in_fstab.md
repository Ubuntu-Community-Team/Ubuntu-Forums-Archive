---
title: "why there is no /dev/sda in fstab"
date: 2008-08-03
forum: General Help
---

### Post by lnthai2002 on 2008-08-03
Hi guys,

I 've just got ubuntu on my laptop and I notice that the device partition column in /etc/fstab which used to be like /dev/sda0 has been replaced by a cryptic string like UUID=391813c4-1c33-445a-af93-eaca5a86db41. What exactly this tring? I suppose it maps to some partition in /dev but how can I know which one. Let say I have not used all of my disk space when I installed ubuntu, now I want to make a partition on the unused space and add mount it to /mount/newSpace, how can I know which dev to run fdisk on?

Hope to get some help soon

Thai

---

### Post by sisco311 on 2008-08-03
you can list the uuid of the partitions with 
the blkid command
```
sudo blkid
```

---

### Post by drs305 on 2008-08-03
In answer to your question as to *why*, the uuid identifier is 'hard-coded' into that partition - it will, generally speaking, never change unless the partition is reformatted. 

Although on laptops the primary partition is not likely to change, the *sda* designations had the possibility of changing when another device or partition was added. This caused problems because fstab doesn't automatically update and account for these changes. 

Partitions can be identified by device/number (sda1), uuid (3GDA56), or label (WINDOWS). Each has it's advantages and drawbacks. if you really hate the uuid concept, you can edit your fstab to use one of the other designations...  ;-)

When you have no more issues or questions about this, please mark the thread SOLVED using the Thread Tools link at the top right of the first post.

---

### Post by bodhi.zazen on 2008-08-03
For info on UUID see :

[http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

sda = the entire hard drive, please see:

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

And for assistance with fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Basically you set which partition you want to automatically mount when you install and if you need to change later, edit fstab.

list partitions by UUID with ;

```
sudo blkid
```

---

