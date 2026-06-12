---
title: "Correct mount point for second hdd"
date: 2010-11-03
forum: Hardware
---

### Post by karogi on 2010-11-03
Hi guys, i am a bit newbie on linux (ubuntu) and i have a problem with my second hard disk.

First, i want say that after i installed ubuntu 10.04, where wasn't any problems with my second hdd. It mounted normally (i was able to see my second hard disk in menu bar "places").

And now some interesting things started...

i was turned off my pc, and after i turned it on, i wans't able to see my another hard disk...

i tried to change something with gparted, or editing with fstab (google power :) ) but nothing...or if it mounted, after restart same **** happens... i can't see my second hard disk.

---

### Post by BlueLionCostas on 2010-11-03
Is this second hdd internal? And could you post your fstab?

---

### Post by karogi on 2010-11-03
AntrasHDD - thats my second hdd name :) My second hdd is internal.


And here is my current fstab. (now i can see my second hdd, but if i do restart, it am getting error on logging screen (incorrect mount point).

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b681ebab-e7f1-4749-a912-659e10d62891 none            swap    sw              0       0
/dev/sdb1      /media/AntrasHDD ntfs    defaults          0        0
```

---

### Post by CharlesA on 2010-11-03
Can you post the output of this command please:

```
mount
```

```
sudo fdisk -l
```

EDIT: The reason it's giving incorrect mountpoint is because that folder hasn't been created yet.

What you could do is create a folder in mnt or media named something like "data" and mount that drive there.

```
sudo mkdir /mnt/data
```

---

### Post by karogi on 2010-11-03
ok, lets look...

mount
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/AntrasHDD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/karolis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=karolis)

```

sudo fdisk -l

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6e69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37785   303499264   83  Linux
/dev/sda2           37785       38914     9069569    5  Extended
/dev/sda5           37785       38914     9069568   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c59e822

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

```

P.S. i am created mount point at /media/AntrasHDD. other 2 mount points "sda1" and "HDD" are other tries. And i dont know how to delete it.
 It looks like this:
[[IMG]http://img835.imageshack.us/img835/9444/nuotraukar.th.png[/IMG]](http://img835.imageshack.us/i/nuotraukar.png/)


EDIT:  I tested now my current fstab. After restart i was able to look my second Hard disk. Now i am restarting pc again...

It looks like i fixed it :) But i am not sure... Does my fstab is correct? if i created mount point at /media/AntrasHDD ??  And how i can delete my other mount points (we can see in screenshot, "hdd" and "sda1" mount points)???

---

### Post by BlueLionCostas on 2010-11-03
Yes, your fstab should be fine now. If you can't delete those other folders by just pressing delete you can do this:
```

sudo rmdir /media/HDD
sudo rmdir /media/sda1
```
That will delete the folders with root privileges, but only when they are empty, preventing you from doing anything stupid on accident ;)

---

### Post by karogi on 2010-11-03
thank you very much :)

P.S. how to edit my tread "prefix" ?? i would like to change it from "ubuntu" to "solved".?  :)

---

### Post by CharlesA on 2010-11-03
Change it from the thread tools menu. :)

---

### Post by BlueLionCostas on 2010-11-03
> **karogi said:**
> thank you very much :)

P.S. how to edit my tread "prefix" ?? i would like to change it from "ubuntu" to "solved".?  :)
You're welcome :)

At the top of the thread you should see 'Thread Tools'. In that menu should be the option to mark the thread solved.

Edit: I need to type faster >_>

---

### Post by karogi on 2010-11-04
Same problem this morning again. my fstab is correct, but on logging screen i got a "mounting error".

And i saw(using "disk utility") that my main hard disk device should be named as "/dev/sda1, but it automatically changed to "/dev/sdb1". 

why hard disk's devices are changing automatically?? what  i should to do that:

the main hard disk device - /dev/sda1
my second hard disk device - /dev/sdb1


Sorry, if my English is complicated :)

---

### Post by jocko on 2010-11-04
> **karogi said:**
> Same problem this morning again. my fstab is correct, but on logging screen i got a "mounting error".

And i saw(using "disk utility") that my main hard disk device should be named as "/dev/sda1, but it automatically changed to "/dev/sdb1". 

why hard disk's devices are changing automatically?? what  i should to do that:

the main hard disk device - /dev/sda1
my second hard disk device - /dev/sdb1


Sorry, if my English is complicated :)
Your problem is that you try to mount it using the device node (/dev/sdX). Device nodes are set on each individual boot, and often change between boots.
That's why UUID's were invented.
Change your fstab to use the correct UUID for the partition.

To find out the UUID, run this command in a terminal:
```
sudo blkid
```It should give you a few lines like this (one for each partition):
```
/dev/sdb1: UUID="[COLOR=Blue]0d76854e-ae85-42be-8840-07ee9fb1b56c[/COLOR]" TYPE="ext4"
```Copy the UUID of the correct partition and paste it into your fstab to make it look like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b681ebab-e7f1-4749-a912-659e10d62891 none            swap    sw              0       0
UUID=[COLOR=Blue]0d76854e-ae85-42be-8840-07ee9fb1b56c[/COLOR]      /media/AntrasHDD ntfs    defaults          0        0
```
I notice you also mount your root partition using only the device node. You may want to change that to UUID also...

---

### Post by karogi on 2010-11-04
it still won't run correctly. Maybe i do something wrong..

sudo blkid

```
/dev/sda1: UUID="717870a7-8606-4ef9-a8e2-19bd7d24b196" TYPE="ext4" 
/dev/sda5: UUID="b681ebab-e7f1-4749-a912-659e10d62891" TYPE="swap" 
/dev/sdb1: LABEL="Antras HDD" UUID="65FA39F90AC82215" TYPE="ntfs" 

```

which type of UUID i should copy for my second hard disk?

---

### Post by BlueLionCostas on 2010-11-04
Your new fstab should probably look like this:```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=717870a7-8606-4ef9-a8e2-19bd7d24b196       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b681ebab-e7f1-4749-a912-659e10d62891 none            swap    sw              0       0
UUID=65FA39F90AC82215      /media/AntrasHDD ntfs    defaults          0        0
```Now please don't just copy it, but look what I did, part because I can't be a 100% sure and part because you should then be able to do it on your own next time :)
Seriously, double check it, because I don't want to be responsible for messing up your system! :P
You might also want to align everything a bit to make it clearer, not that it really matters.

---

### Post by karogi on 2010-11-04
with second try my fstab looks same. looks like we have fixed it. 
thanks again. :)

---

### Post by BlueLionCostas on 2010-11-04
> **karogi said:**
> with second try my fstab looks same. looks like we have fixed it. 
thanks again. :)
No problem, you're welcome :) Glad to hear you got it fixed.

---

### Post by karogi on 2010-11-14
One simple question. If i want mount my second hard disk at /media/Antras HDD, Can i write in fstab this
```
UUID=xxxxxxxxxxxxx   /media/Antras-HDD    ntfs   defaults   0    0
```

Mount point "/media/Antras-HDD" because i need space after word "Antras" :)

---

