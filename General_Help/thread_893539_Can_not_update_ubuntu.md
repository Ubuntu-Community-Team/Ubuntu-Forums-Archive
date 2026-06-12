---
title: "Can not update ubuntu"
date: 2008-08-18
forum: General Help
---

### Post by Gondee on 2008-08-18
Im sure this has been posted before, but i was not able to get the right tags so here it goes. Every time i try to update i get this error
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Then when i go to manually configure it it gives me this
```
josh@josh-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1

```

Sooo, yeah. :confused:    Im fairly new to ubuntu so this could be somthing easy but o well. 

thanks in advance for any help i can get =)

---

### Post by cdtech on 2008-08-18
> gzip: stdout: No space left on device

Looks like your "/" might be full. Lets see the output of:
```
df -H
```

---

### Post by LinuxRocks713 on 2008-08-18
If your hard disk is full, you should try to clean out as much as possible, or you will **not** be able to login the next time you start your computer because of a bug in GNOME.

---

### Post by Gondee on 2008-08-18
It was a fresh install, today actully. I did it really fast so i might have got confused or somthing
```
josh@josh-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               75G   3.0G    68G   5% /
varrun                 1.8G   119k   1.8G   1% /var/run
varlock                1.8G      0   1.8G   0% /var/lock
udev                   1.8G    58k   1.8G   1% /dev
devshm                 1.8G    13k   1.8G   1% /dev/shm
lrm                    1.8G    41M   1.7G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2               48M    43M   3.0M  94% /boot
gvfs-fuse-daemon        75G   3.0G    68G   5% /home/josh/.gvfs
josh@josh-desktop:~$ 

```

Thanks for the replies guys

---

### Post by cdtech on 2008-08-18
Your /boot directory is full and cannot hold any more kernel images. You have to resize your /boot directory using the "gparted live cd". 48M is really not a whole lot of space for a /boot directory (thats about enough space for one kernel image). You need at least 200 to 400M of space, just enough to play around with a few kernel images.

---

### Post by Gondee on 2008-08-18
oo, i had a feeling it was something easy. 

What would you recommend for the partition sizes of a 80 Gig hard drive?

I thought i remembered reading some where that boot was supposed to be 50 megs 2 gig swap file and the rest /root

---

### Post by cdtech on 2008-08-18
Personally I use 1G for my "/boot" (cause I like playing with kernels and keeping several around). You would be ok with 200M, that will allow you to have about 4 each images within your "/boot" directory. 

If you plan on installing a lot of app's your "/" partition should be around 20G. I have mine set at 40G because I have the space. I've used 20G already with all the app's I have installed. 

I use another 20G for my "/home" directory but if you store your media (videos, pict's, music) on a shared drive then you probably would not use that much space.

The rest of the space on my drive I've formated to an NTFS partition and use it to share between my Vista and Ubuntu (media).

It really depends on your preference I guess. If you plan the layout in the beginning it saves you from having to resize your partitions later (depending on how much data you have, it could take hours to resize partitions).

I hope this helps........

**Update::.**
As far as your "Swap" I have 2G of memory and probably use no more than 700M with a few programs operating at the same time. If I wanted to Hibernate I would need at least 1G to save image to disk. I settled for 2G for my "Swap" just to be safe.

---

### Post by Gondee on 2008-08-18
thanks for all the help.

I have 4 gigs of ram so i think ill be fine with a 1 gig swap.

---

