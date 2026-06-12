---
title: "Wubi installation problems"
date: 2008-10-29
forum: General Help
---

### Post by dharmabum4732 on 2008-10-29
Hello,

I've been having some trouble installing Wubi, and I wonder if anyone has any ideas that might help.

I understand that with 8.10, Wubi should work even with software raid, but I think that this might be the source of my trouble, as I use raid 0.

After searching through this forum for a solution, I noticed that posting the output of the following might be helpful in determining my problem.

Cat /proc/cmdline
```
debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/intrepid-desktop-amd64.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=US console-setup/variantcode= --   ROOTFLAGS=syncio
```

Cat /proc/partitions
```
Major Minor #blocks name
8 0 312571224 sda
8 1 625135616 sda1
8 16 312571224 sdb
8 32 117220824 sdc
8 33 117218304 sdc1
8 48 87685784 sdd
8 49 97683456 sdd1
8 64 488386584 sde
8 65 488383488 sde1
```

Cat /proc/mounts
```
rootfs . rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,mode=775 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/sdc1 /isodevice fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
```

grep err /casper.log
```
Could not find the installation files...
```
This was followed by a long message that suggested running "chkdsk /r" on windows, which I subsequently did. I also defragmented the disk.

grep mount /casper.log
```
/scripts/casper-premount/30custom_installation: line 101: cannot open /dev/sdx:
No medium found
```

I hope the above information is relevant.

What should I do next?

Thanks,
-Max

---

### Post by ago on 2008-10-29
uninstall, run chkdsk /r, reinstall in verbose mode
if it happens again, copy casper.log to /isodevice (= C: )
then post it here.

---

### Post by dharmabum4732 on 2008-10-29
Hi Ago,

Thanks for your response.

I will follow your advice, and post the results if necessary.

Thanks,
-Max

---

### Post by dharmabum4732 on 2008-10-30
Hello,

I uninstalled Wubi, ran chkdsk /r, and reinstalled in verbose mode, but I'm still encountering the same problem.  
It looks like I will need to post the casper.log, but I'm not sure how to copy it to /isodevice (=C:). (Sorry, I'm a bit of a novice)

How do I copy casper.log while I'm stuck in the busybox?

Thanks,
-Max

---

### Post by dharmabum4732 on 2008-10-31
Update:

I attempted to follow some instructions for copying casper.log, which I found in another thread

```
mkdir /winpart
mount /dev/sda1 /winpart #assuming the windows partition is on sda1
cp casper.log > /winpart/casper.log
```

When I tried it, it said "invalid argument" after typing "mount /dev/sda1 /winpart"

---

### Post by ago on 2008-10-31
try 

mount -t ntfs /dev/sda1 /winpart

---

### Post by dharmabum4732 on 2008-10-31
Thanks again for your reply, Ago,

I tried your advice, but I'm still encountering problems.  Here is the result of trying "mount -t ntfs /dev/sda1 /winpart" :

```
NTFS signature is missing
Failed to mount '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device?  Or the whole disk instead 
of a partition (e.g. /dev/hda, not /dev/hda1)?  Or the other way around?
```

Would it be possible to copy the casper.log to a usb device instead of to sda1?  Maybe then I could at least post the results of casper.log.

Thanks again for your advice!  Please let me know what you think,
-Max

---

### Post by ago on 2008-10-31
Raid should work in theory but it has been thinly tested at this point (and in particular I have no raid...). 

The error above either means that sda1 is not ntfs, or that it is a raid problem.

Did you actually install in sda1, can you try another partition? If you want to play with the raid, search the forum for "dmraid"

---

### Post by dharmabum4732 on 2008-10-31
Hello,

Thanks for all of your help, Ago.  I will try to search for dmraid to see if I can find a solution that way.

All the best,
-Max

---

### Post by Cranders on 2008-11-06
Did you ever find a solution to installing Wubi on a RAID 0 system? I am having the same problem.  I originally tried this with 8.04 but have recently downloaded 8.10 (which should support RAID) and have the same problem as before.

Thanks, Chris

---

