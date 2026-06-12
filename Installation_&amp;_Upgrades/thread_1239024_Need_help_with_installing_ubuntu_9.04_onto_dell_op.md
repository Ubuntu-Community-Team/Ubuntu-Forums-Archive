---
title: "Need help with installing ubuntu 9.04 onto dell optiplex gx280"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by Ghostnik11 on 2009-08-13
Hi so I want to install ubuntu 9.04 onto a dell optiplex gx280 desktop but after booting from a livecd when I click on install an error comes up when it comes up to the prepare partitions section.  It says no root file system is defined.  I Want to know What should I do so I can install ubuntu onto the optiplex gx280?

Thanks in advance.

---

### Post by sblunix on 2009-08-13
Are you manually partitioning the drive?

If so, make sure whichever partition you want your root to be has the mountpoint "/" and is formatted...

also don't forget some swap space, and the root partition should be Ext3...

---

### Post by Ghostnik11 on 2009-08-13
> **sblunix said:**
> Are you manually partitioning the drive?

If so, make sure whichever partition you want your root to be has the mountpoint "/" and is formatted...

also don't forget some swap space, and the root partition should be Ext3...
thats the thing i think i have to manually partition the drive but the thing is that the hard drive does not even show up when i put things like sudo fdisk -l.  So my main problem is that i need to learn how to first find the hard drive then I want to wipe it clean b/c I think it is corrupt b/c it had windows XP on it and crashed.  Its my mom computer and she just wants it fixed so I know that the only thing that can fix it is ubuntu (linux).  So would you know how to first find the hard drive then want to know how i would wipe the hard drive clean.  Thank you for taking time out to help.

---

### Post by zkriesse on 2009-08-13
Well to start with is your BIOS set to boot from and run from CD-Drive? And does the BIOS even recognize the hard drive?

---

### Post by Ghostnik11 on 2009-08-13
> **Zachk18 said:**
> Well to start with is your BIOS set to boot from and run from CD-Drive? And does the BIOS even recognize the hard drive?
My bios is not set to boot from cd but I press control + Alt + F8 at start up screen then selected boot from cd and thats how i was able to boot ubuntu 9.04 and my bios does not recognize the hard drive. thanks for the help.  so how do i get my bios to recognize my hard drive.

---

### Post by ghpk on 2009-08-13
check if your Bios shows any HDD ?
check if you are able to check if any loose cable connections inside the main CPU unit.

If the HDD is not getting detected it can be a loose connection or the HDD is toasted.

---

### Post by Ghostnik11 on 2009-08-13
> **ghpk said:**
> check if your Bios shows any HDD ?
check if you are able to check if any loose cable connections inside the main CPU unit.

If the HDD is not getting detected it can be a loose connection or the HDD is toasted.
Well i don't think the hard drive is toasted b/c when I type df in the terminal I get this:

> ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   513068      2392    510676   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                   513068      2392    510676   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                   513068         0    513068   0% /lib/init/rw
varrun                  513068       104    512964   1% /var/run
varlock                 513068         4    513064   1% /var/lock
udev                    513068       136    512932   1% /dev
tmpfs                   513068       128    512940   1% /dev/shm
rootfs                  513068     67604    445464  14% /
/dev/sr0                715732    715732         0 100% /cdrom
/dev/loop0              691328    691328         0 100% /rofs
tmpfs                   513068        12    513056   1% /tmp


the thing is I don't know how to mount the hard drive after getting this info.  thanks for the help

---

