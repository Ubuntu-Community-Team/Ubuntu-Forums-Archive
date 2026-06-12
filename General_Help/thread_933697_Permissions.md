---
title: "Permissions"
date: 2008-09-29
forum: General Help
---

### Post by Comhra on 2008-09-29
I partitioned my External drive in Mac OS X and devoted one of the p[artitions to Ubuntu.  Changed the permissions to read and write, unticked the: Ignore ownership box ...no problems you would think.
Ubuntu can't write to the partition,

Tried: sudo chmod 777 /media/Linux...permissions changed says Terminal.  Ubuntu still can't write to the partition.

How can I enable Ubuntu to read/write to this partition?

---

### Post by mindoms on 2008-09-29
whats the error message?

Is the disk mounted read-only?
```

cat /proc/mounts | grep /media/linux
ls -ld /media/linux

```
please post the output

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

### Post by Comhra on 2008-09-30
cat /proc/mounts | grep /media/disk
/dev/sdb3 /media/disk ext3 rw,nosuid,nodev,relatime,data=ordered 0 0

---

### Post by Comhra on 2008-09-30
ls -ld /media/disk
drwxrwxrwx 3 root root 4096 2008-09-30 18:31 /media/disk

---

### Post by Comhra on 2008-09-30
Solved it or rather, worked around it.  Tried Extension 3 in Gparted, Ubuntu still couldn't write to it and Mac wouldn't even mount it.  

Erased and formatted to MS Dos of all things thinking that Ubuntu, being a lot more versatile in this and other areas that it would mount, read and write to a Dos partition.  I was gambling that the permissions would resolve themselves and sure enough it worked. 

I now have a back up of all my Ubuntu Data, a bootable back up of Tiger, a third partition for my Mac data and I'm ready for the Ibex.

What I'd like to do is create a Home partition but since I've failed three times already, it's going to be a job for another day.  I don't want to brick a rock solid Hardy installation.

You know what, sometimes Mac really sucks.

---

