---
title: "Deleting Vista Partition That Is the First Partition"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by plinydogg on 2008-12-19
Hi folks,

I'm currently dual booting with Vista and Ubuntu. My first partition has Vista and my second one has Ubuntu. I want to get rid of the Vista partition but am wondering if there are any issues I need to worry about since Vista is the main partition?

My plan at this point is to open up gparted, delete the partition, resize my Ubuntu partition a little bit, and then create a new EXT3 partition with most of the old Vista space (i.e., two partitions: one for data storage and one for the OS).

I'm expecting that doing this, though, will cause some sort of GRUB error. What do I need to do to ensure that this doesn't happen? 

Alternatively, I was also considering simply doing a fresh install, but I feel like I've got too many random settings in place that would be difficult to get up and running again...

Any thoughts are much appreciated!

---

### Post by taurus on 2008-12-19
If you plan to use gparted, you have to use either the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), since you cannot resize the partition that you are using.

---

### Post by plinydogg on 2008-12-19
Good point taurus!

One more thing: if I go the clean install route and choose to use the entire disk for the Ubuntu install, will the fact that I've overritten the Vista partition cause problems with GRUB, or will it be okay since GRUB will be reinstalled?

Thanks again!

---

### Post by logos34 on 2008-12-19
I don't see any pitfalls, but if ubuntu is on a logical partition you have to first expand the extended partition which frames it before you can grow the ubuntu root partition inside.  Also, you'll have to work from gparted on the ubuntu live cd since root cannot be mounted during resize operations (edit: as taurus just pointed out).

Remember to remove any windows entries from /etc/fstab 

If for some reason you get a Grub error on restart, you can reinstall it from the live cd (see link in my signature)

---

### Post by plinydogg on 2008-12-19
Fantastic! Perhaps I'll give it a whirl. So long as I can perform a clean install if everything goes wrong, I should be okay (i.e., I'm just trying to avoid the situation where my computer becomes a brick). 

Just so I'm clear, you're suggesting that I edit /etc/fstab before while in Ubuntu normally, and only then reboot and mess with gparted?

Thanks!

---

### Post by logos34 on 2008-12-19
yes, delete vista, then 

gksudo gedit /etc/fstab

to remove any windows lines.  That way it won't try to automount them when you reboot into ubuntu.  Then boot the live cd and use gparted there like taurus suggested to grow ubuntu to the front of the disk

---

### Post by plinydogg on 2008-12-19
Fantastic! I'll try it once I get home from work!

---

### Post by plinydogg on 2008-12-19
Uh oh. I deleted the Vista partition, edited fstab, booted into the LiveCD and attempted to resize the Ubuntu partition. It seemed to go fine until I got some sort of error at the end. It looks like the operation was a partial success: the partition is the desired size (72.67 GB) but all of the new space appears to be used (i.e., it says that 69 GB is occupied)!

---

### Post by taurus on 2008-12-19
Can you post the screenshot of gparted (from the LiveCD, of course) and also the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by plinydogg on 2008-12-19
Oops, taurus, I didn't see your response until now(!). Things worked out great in the end, I just did a clean install and all is well. I really appreciate everyone's help!

---

