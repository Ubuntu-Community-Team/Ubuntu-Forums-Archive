---
title: "Merging two partitions"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by lsutiger on 2008-01-16
I am trying to merge 2 partitions on my hard drive.I was going to dual boot, but I decided just tto use virtual box instead. Back to the problem.
The order of the partitions are as follows:
sda1 - boot and /
sda2 - home
sda3 - swap
sda4 - empty partition

I am attaching a screenshot to let you know what I am working with.

I want to merge sda2 and sda4. Is that possible?

I can not unmount sda2 or the swap, neither can I resize sda2.

Thanx in advance!

---

### Post by lgambett on 2008-01-16
sorry, AFAIK merging two partitions it is not possible. But.... why you cannot resize your second partition ?

---

### Post by lsutiger on 2008-01-16
The option is greyed out...do not know why.

---

### Post by lgambett on 2008-01-16
Maybe your partition contains an ext3 partition. Parted cannot resize ext3 partitions.
If this is the case you can;
- convert the ext3 partition to ext2 with 
**tune2fs -O ^has_journal /dev/xxx.**

Now you should be able to resize the partition.

- convert it back to ext3 with 
**tune2fs -j /dev/xxxxx**

---

### Post by ajgreeny on 2008-01-16
Use gparted on the live CD and you can do all you want, but not in one action.
1   First copy all the files in sda4 to sda2, /home.  I see you say sda4 is empty but gparted shows 758 MB used, though that may just be the file system use.
2   Now delete the sda4 partition and then the swap file partition, sda3, or try to move swap to the end of the disk, if that is possible. I think it should be, but have never tried it with a swap partition, only ext3 file systems, where it works well.
3   If it moves great, now just enlarge the sda2 partition.  It it won't move, just enlarge the sda2 partition almost to the end of the disk, but save 972MB for the swap right at the end and when you've enlarged the sda2, simply make a new sda3 into the swap file, by formatting the 972MB at the end as swap.
4   You will now need to either find the UUID of the partitions and edit your /etc/fstab, or you can just edit before rebooting using the live CD again and not using UUIDs at all but just the /dev/sdaX naming convention, which still works in the fstab file OK.

I hope that all makes sense to you and if you do try it, good luck.  Just make sure you BACKUP first, just in case.

---

### Post by lsutiger on 2008-01-18
```
udo tune2fs -O ^has_journal /dev/sda2
tune2fs 1.40.2 (12-Jul-2007)
The has_journal flag may only be cleared when the filesystem is
unmounted or mounted read-only.

```

The dev I need to enlarge is the one I setup at install as my home folder.
> I hope that all makes sense to you and if you do try it, good luck. Just make sure you BACKUP first, just in case.
__________________
Last edited by ajgreeny : 1 Day Ago at 04:57 PM.
Thanks

I can't seem to get GPARTED to work correctly, no matter what I choose at boot. Either the screen is messed up or the mouse quits working

---

### Post by ajgreeny on 2008-01-18
Are you using the ubuntu liveCD for gparted or have you got the gparted liveCD?  Which ever one you are using and not having success, try the other.  The gparted liveCD is certainly worth having around at any time and it's only a 30MB download.  Well worth downloading and keeping handy.

---

### Post by lsutiger on 2008-01-18
Loaded with gparted, but nearly went blind. No matter what I chose to boot, it jacked up the screen. But I got it done. Thanx

---

### Post by ajgreeny on 2008-01-18
No problem.  No doubt your difficulties with the graphics are down to your graphics card - an ATI which just about gives the most difficulties with driver installation in many situations.
Glad you got it fixed, and also pleased I was right that gparted could do it - was it the latest gparted live CD or the version on the ubuntu liveCD?

---

### Post by lsutiger on 2008-01-18
the latest and greatest gparted cd from souceforge

---

