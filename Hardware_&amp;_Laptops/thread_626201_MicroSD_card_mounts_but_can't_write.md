---
title: "MicroSD card mounts but can't write"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by dmgthe2nd on 2007-11-28
Hi,

So I'm using a microSD SanDisk card with an SD adapter that fits into my SD card reader (internal Vostro 1500 reader).  I can read/write normal SD cards with the same internal card reader.  When I pop in the MicroSD, Ubuntu mounts it and I can see all the files.  When I try to write on the card (copy a song or two) an error message comes up saying "Error "Operation not permitted" while copying.."

Do I need to reformat the microSD card or something?

Thanks for all the help to come!!

---

### Post by PmDematagoda on 2007-11-28
What is the filesystem on the MicroSD card?

---

### Post by dmgthe2nd on 2007-11-29
I believe its vfat.  I did the df -T code in the terminal when it was mounted and thats what came up.  Although, it did say % used was 100%.

---

### Post by PmDematagoda on 2007-11-29
> **dmgthe2nd said:**
> I believe its vfat.  I did the df -T code in the terminal when it was mounted and thats what came up.  Although, it did say % used was 100%.

Is the MicroSD card being used fully? If so then that is your problem.

---

### Post by dmgthe2nd on 2007-11-30
Sorry I failed to mention that I couldn't write at 90% full and I still can't at 0% full.  I have a feeling the system thinks the card is full when it is not.

---

### Post by PmDematagoda on 2007-11-30
Can you post the output of:-

```
cat /etc/mtab
```

---

### Post by dmgthe2nd on 2007-11-30
As I was writing this reply, I decided to make sure the card didn't work.  And, for some reason, it DOES!!
I can copy anything onto the media now with success.
I don't know why it wouldn't work before....
But thanks for your help!


```
david@david-laptop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/mmcblk0p1 /media/KODAK vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

```

and here is df -T
```
david@david-laptop:~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext3   110903204  62884372  42385240  60% /
varrun       tmpfs      777180       104    777076   1% /var/run
varlock      tmpfs      777180         4    777176   1% /var/lock
udev         tmpfs      777180        92    777088   1% /dev
devshm       tmpfs      777180         0    777180   0% /dev/shm
lrm          tmpfs      777180     34696    742484   5% /lib/modules/2.6.22-14-generic/volatile
/dev/mmcblk0p1
              vfat     1983360         0   1983360   0% /media/KODAK

```

The microSD would be the last one there.  I was wrong about the 100% full thing.

---

### Post by PmDematagoda on 2007-11-30
What a very strange thing:-k, at least the problem was solved, that is the main thing:).

---

### Post by berliita on 2007-12-05
Unfortunately, i experience the same problem with my newly purchased SanDisk Cruzer Titanium USB Flash Drive (4.0 GB), which is in almost pristine condition. Before i go into details, let me note that the drive works flawlessly on OpenSuse 10.2 . My Ubuntu version is Gutsy Gibbons.


The symptoms:

When i plug the drive into the USB port of my PC, the driver's front lights up, as it's supposed to, and a "SanDisk U3 Titanium" icon appears on my desktop. Then an error message pops up:
```
Cannot mount volume.
Unable to mount the volume.
Details:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so
```

Then the driver's window opens, displaying the preinstalled files, which i'm able to copy to my desktop. But files copied to the drive in OpenSuse are not shown in the window. And when i try to drag a file from my desktop into this window, the following error message pops:
```
Error while copying to "/media/US System". You do not have permissions to write to this folder.
```

The "Permissions" tab of the drive's properties window indicates that "owner" (me), "group" (root) and "others" - all have only file access permissions. When i try to change the owner access permissions to "Create and delete files", the following error message pops:```

The permissions could not be changed.
Couldn't change the permissions of "U3 System" because it is on a read-only disk
```

Additionally, the "Basic" tab of the properties window associated with the driver indicates that the driver is full:
```
5.4 MB used
0 MB free
```
But, as i wrote above, the driver is brand new, and, moreover, its capacity is 4.0 GB.

Here's the output of my running "cat /etc/mtab":
```
$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/scd1 /media/U3\040System iso9660 ro,nosuid,nodev,uid=1000,utf8 0 0

```

---

