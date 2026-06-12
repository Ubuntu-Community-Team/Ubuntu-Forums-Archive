---
title: "Nautilus won't let me delete....the meanie!"
date: 2005-11-16
forum: General Help
---

### Post by topmate on 2005-11-16
Am REALLY enjoying playing around with Ubuntu and have now switched to it on my main desktop, happily replacing (cough, cough) xandros oce. Hey, you've gotta start somewhere, right?

I've been merrily mounting and formatting various partitions this evening, but am having trouble with a new ext3 partition that I created as root via the graphical disk manager. I've mounted the partition, have added the following line to fstab for it - 

/dev/hdb5	/media/disk1	ext3	rw,defaults,user	0	0

and have run chmod and chown on both /dev/hdb5 and /media/disk1. I can write to the partition without a problem. but once its on there I can only delete it as root.

So, I'm a little stumped as to why I'm able to write to the partition but not delete files once they're there. Any thoughts?

---

### Post by Kyral on 2005-11-16
chown -R the disk? While its mounted of course

---

### Post by topmate on 2005-11-16
[QUOTE=Kyral]chown -R the disk? While its mounted of course[/QUOTE]

Nope, no joy with that, already tried that one, should have said. All very confusing!

---

### Post by Kyral on 2005-11-16
```
/dev/sda1       /anime          ext3    defaults,user_xattr,owner,rw  0       2
```

Try that (its the line from my fstab slightly modified) replacing /dev/sda1 and /anime with your things of course

---

### Post by topmate on 2005-11-17
[QUOTE=Kyral]```
/dev/sda1       /anime          ext3    defaults,user_xattr,owner,rw  0       2
```

Try that (its the line from my fstab slightly modified) replacing /dev/sda1 and /anime with your things of course[/QUOTE]

Yep, that's sorted it. Still not completely sure why that would work where my fstab didn't, but hey its working now, I'll worry about why later! :)

---

