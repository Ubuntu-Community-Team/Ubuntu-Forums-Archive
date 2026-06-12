---
title: "Help: Fine RAID mess..."
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by zoiks on 2009-04-10
OK my RAID configuration is a little messed up now. I used to have a nice setup where I booted up with a root filesystem that was RAID 1. (That way the initial kernel could load up without md on sda1, load up md, and then re-mount the root partition as a RAID 1 device.) This setup was arranged using the "alternate" installation CD for mythbuntu (8.04). That's the setup I'm trying to get back to.

Anyhoo, long story short, my current partition setup is as follows. I have four drives, each with 2 partitions: (all filesystems are ext3)

sda, sdb, sdc, sdd

The second partition of each of these drives is a member of a 4-device RAID5 array (/dev/md1). That's working fine. The first partition of each (identically sized) drive is as follows:

sda1 -> currently used as / filesystem, booted into
sdb1 -> first member of /dev/md0 RAID1 array
sdc1 -> second member of /dev/md0 RAID1 array
sdd1 -> currently unused
grub is installed on boot sector of sda1 and points to sda1 as root filesystem partition

Here is /proc/mdstat
```
~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sda2[0] sdd2[3] sdc2[2] sdb2[1]
      2109663552 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md0 : active raid1 sdb1[0] sdc1[1]
      19534912 blocks [2/2] [UU]
      
unused devices: <none>

```

and here is /etc/mdadm/mdadm.conf:
```
~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md1 level=raid5 num-devices=4 UUID=xxxxxxxx:xxxxxxxx:xxxxxxxx:xxxxxxxx
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=xxxxxxxx:xxxxxxxx:xxxxxxxx:xxxxxxxx

# This file was auto-generated on Sun, 11 May 2008 22:31:33 +0000
# by mkconf $Id$

```

What I would **like** the setup to be (excluding the RAID5 array) is

sda1 -> first member of md0, booted into
sdb1 -> second member of md0
sdc1 -> unused
sdd1 -> unused
grub installed on boot sector of sda1 and using /dev/md0 as root filesystem

I just don't know how to get from here to there. (Actually I'd like to expand the / device to be a 4-mirror array for better read performance, but I'd be happy at this point with just getting to a 2-device mirror.)

This is, in fact, how it was set up until recently when I started messing with it. By "messing with it" I mean I tried to make md0 a 3-device RAID1 mirror array (for higher read performance). When I did that, it would not boot, instead giving me "md0 stopped" during the boot process and dropping me to busybox.

Not exactly sure why it failed when I did that (I did correctly edit the /etc/mdadm/mdadm.conf file and grub was directed to boot from /dev/md0). Luckily, though, since everything is mirrored I could still recover my / partition.

One thing I tried was to mirror the data on /dev/sda1 to /dev/md0 using

```
cp -dpRx / /mounted_md0/
```

and then edit the grub menu during boot to point to /dev/md0 as root device. No go, it gives up waiting for the root device and drops me to busybox/initramfs. Not sure why.

Another thing I tried was to mirror /dev/sda1 to /dev/md0 (as above) and then tell grub to use /dev/sdb1 as root filesystem, while having /dev/md0 mounted to "/" in /etc/fstab. (!!!) It sorta worked, in that the system booted up, but **I ended up in some alternate universe** as [COLOR="Red"]'cat /proc/mdstat' told me md0 was inactive and sdb1 was missing from its list, while 'df' said /dev/md0 was mounted to / and currently being used![/COLOR] :confused: I kid you not! WTH???

Any help is hugely appreciated! :-)

---

### Post by zoiks on 2009-04-11
Well, I found the information I needed through this very helpful and detailed HowTo from Zafrusteria:

[http://ubuntuforums.org/showthread.php?t=1027240](http://ubuntuforums.org/showthread.php?t=1027240)

In fact, going through the steps made me realize why I had messed up my RAID1 root device to begin with. I had neglected to run

[B]update-initramfs -u
[/B]
after adding the new device to the RAID1 array. Well, now I know. :) Now it's all up and running flawlessly.

---

