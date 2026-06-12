---
title: "Extra HDD problems"
date: 2008-12-04
forum: Hardware
---

### Post by burstonit on 2008-12-04
Hi all - my first post.
I recently installed 8.04 on my PC - dual boot with XP - two sata HDD of 500 gig. It all works fine although setting up my network was a bit of a chore.
Last night I decided to add an old HDD (120 gig) that I had unused.
I eventally managed to get it installed and formatted and it appears in the available drives after I have started Ubuntu.
The problem is that when I try to write data to it it will not let me.
I have tried unmounting it and remounting it which has no affect.
Any ideas anyone.

Thanks
Richard

---

### Post by fernandohleme on 2008-12-04
Hi

I would try to change permissions writen over the hardware.
typing gksu nautilus, searching for the drive and changing permissions in its properties.
It may solve your problem...

---

### Post by taurus on 2008-12-04
What filesystem is that harddrive and how do you mount it, from a terminal or through /etc/fstab?

---

### Post by burstonit on 2008-12-05
Taurus - the drive is ext2 and I mount/unmount by right clicking and using the menu that pops up.
Should I have used ext3 ???

Richard

---

### Post by stefangr1 on 2008-12-05
> **burstonit said:**
> Hi all - my first post.
I recently installed 8.04 on my PC - dual boot with XP - two sata HDD of 500 gig. It all works fine although setting up my network was a bit of a chore.
Last night I decided to add an old HDD (120 gig) that I had unused.
I eventally managed to get it installed and formatted and it appears in the available drives after I have started Ubuntu.
The problem is that when I try to write data to it it will not let me.
I have tried unmounting it and remounting it which has no affect.
Any ideas anyone.

Thanks
Richard

I think I understand what you mean.

You might have to change your fstab (make an update before you change anything!) by running sudo nano /etc/fstab

You probably see your drive there, like below (or with an UUID)
/dev/sdb1 /media/med4 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2

you can try add some options there, like rw

---

### Post by taurus on 2008-12-05
> **burstonit said:**
> Taurus - the drive is ext2 and I mount/unmount by right clicking and using the menu that pops up.
Should I have used ext3 ???

Richard

You can leave it as ext2.  Now, all you have to do is change the ownership of the mount point for that drive from root to your username so you can write to it anytime you want.  Assuming you mount that harddrive to /media/sdb1 and your login name is richard, you could do something like

```
sudo chown -R richard:richard /media/sdb1
ls -la /media
```
And personally, I would use this entry in /etc/fstab for that harddrive.

```
/dev/sdb1   /media/sdb1   ext2   defaults   0   2
```
Or you can replace /dev/sdb1 with the UUID for it.

```
sudo blkid
```

---

