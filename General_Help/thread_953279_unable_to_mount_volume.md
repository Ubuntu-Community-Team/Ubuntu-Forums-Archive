---
title: "unable to mount volume"
date: 2008-10-20
forum: General Help
---

### Post by nicker on 2008-10-20
I'm trying to get my Ubuntu machine back up and running.  When I first tried booting it up I rand into a Grub error.  I tried using supergrubdisk to fix Grub or reinstall it.  From the command line the system wasn't able to find /boot/grub/stage1 or any other necessary files.  I have the Ubuntu LiveCD up and running right now.  The LiveCD can see the hard drive but I'm unable to mount it.  

When trying to mount it I get this error

mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try demesg | tail or so

I did dmesg | tail and got this 
EXT3-fs: invalid journal inode

I also tried 
sudo fsck -t ext3 /dev/sda1
and got this message
fsck.ext3: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

Clearly, something is messed up.  From searching around it sounds like the journal got screwed up somehow or is missing.  

I haven't been able to figure out what the next steps are.  Does anyone have any suggestions?

Thanks for you help.

---

### Post by mempman on 2008-10-20
I think I've run into similar problems before.  I think it was caused by me dual booting my computer and when I was booted into my alternate OS, the computer crashed on me, but the drive, i think, was still mounted under my alternate OS.

Have you tried to force an unmount, because that error fsck is giving you is prolly due to the fact that you can't run fsck on a mounted harddisk.

---

### Post by mempman on 2008-10-20
I believe to force an umount, it is:

```

umount -f

```

---

### Post by nicker on 2008-10-20
So, I don't have a dual boot if that matters.  I only have Ubuntu on the disk.  

I tried doing 
sudo umount -f /dev/sda1
and I get an invalid argument and it says the drive isn't mounted

---

### Post by unutbu on 2008-10-20
Could you please post the output of 
```

mount
```

Also, do you have any idea why this is happening?
Was there a power outage, for example?
Knowing something about the cause of the problem might
help us better troubleshoot the situation.

---

### Post by nicker on 2008-10-21
The output of 
```

mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

```

As far as what caused the problem, I'm not completely sure.  I haven't used this machine in several months.  I tried to use it again now and I started having these problems.  My guess is that it was turned off or unplugged incorrectly or some sort of power failure.

---

### Post by nicker on 2008-10-21
Should I simply add a new line into /etc/fstab or /etc/mtab ?

---

### Post by shawnrgr on 2008-10-21
what was the grub error you received ?

---

### Post by nicker on 2008-10-21
I get a grub error 25 when booting.  I then tried using supergrubdisk with commands
find /boot/grub/stage1 
and
find /grub/stage1

Both returned grub error 15

---

### Post by nicker on 2008-10-21
Here's some other outputs if it helps
```

cat /etc/fstab

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```

```

sudo fdisk -l

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f839f83

Device      Boot   Start   End   Blocks    Id   System
/dev/sda1    *      1      12096  97161088+  83   Linux
/dev/sda2           12097  12188  738990     5    Extended
/dev/sda5           12097  12188  738958+    82   Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

Device   Boot   Start   End   Blocks      Id  System
/dev/sdb1         1      7476  60050938+  83  Linux

```

---

### Post by unutbu on 2008-10-21
Please run
```
sudo dd if=/dev/sda of=dd.out count=20
```
and post dd.out

This is mainly just a test to see if you can pull data from the sda drive at all. If you can, then perhaps the problem is software related and can be fixed. If you can't then perhaps the drive is failing.

---

### Post by nicker on 2008-10-21
Thanks for all the help so far

Here's the output of
sudo dd if=/dev/sda of=dd.out count=20

```

20+0 records in
20+0 records out
10240 bytes (10 kB) copied, 0.000241462 s, 42.4 MB/s

```

---

### Post by unutbu on 2008-10-21
Please post the output of 
```

cd
mount
sudo fsck -t ext3 /dev/sda1

```

---

### Post by nicker on 2008-10-22
Here's the output

```

ubuntu@ubuntu:~$ cd
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devtps (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal /dev/sda1


```

---

### Post by unutbu on 2008-10-22
nicker, I don't know for sure the solution to this problem. I'm not an expert; most of what I know simply comes from googling "attempt to read block from filesystem resulted in short read while checking ext3 journal". 

The only advice I found was to clear the journal. The problem with this is, if the journal contains any transactions that have not yet been written to disk, then you will suffer some data corruption. One webpage warned of "severe" data corruption. 

The journal keeps a log of writes to the disk. If a file is modified or moved, that action is recorded in the journal. It sounds to me like your journal is cut short, not in the proper format. If this is the case, and if there is no way to repair the journal, then the information in the journal and the information that never got written to the journal is already lost. If my interpretation of the situation is correct, then the data corruption has already happened and there is nothing really you can do about it.

The safest thing you could do is use [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) to clone your /dev/sda1 partition. Then do the recovery work on the cloned copy. The advantage of doing this is if clearing the journal results in severe data loss, you still have the original copy of your partition and can try some other method (See the link below).

Well, after all that spiel, I believe the commands to remove the journal are:
```

sudo debugfs -w -R "feature ^needs_recovery" /dev/sda1   # remove the needs_recovery flag
sudo tune2fs -O ^has_journal /dev/sda1                   # remove the journal
```

Then try 

```
sudo fsck -v /dev/sda1     # check/repair the filesystem
sudo tune2fs -j /dev/sda1    # Add an ext3 journal to sda1
```

See [http://osdir.com/ml/file-systems.ext3.user/2005-04/msg00010.html](http://osdir.com/ml/file-systems.ext3.user/2005-04/msg00010.html)
and [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) This link describes other methods for recovering data from a damaged filesystem. See PhotoRec, for example.

Good luck.

---

### Post by nicker on 2008-10-22
This is great, thanks.  I'm assuming since I hadn't used the machine for at least several weeks or a month before this happened that all changes should have been written to the disk.  So, I'm thinking I don't necessarily need to be worried about any transactions in the journal that haven't been written to disk.  

Either way this sounds like a good path to follow so I'll try to clone the partition first and then clear the journal to see if that helps.

Hopefully, I can get to this later tonight after work.  Thanks for the suggestion.

---

### Post by mathgirl on 2011-02-17
I had exactly this problem and was able to fix it with your advised commands.  Thank you!

Two notes:

1) At first when I tried to run fsck, it still said sda1 was busy, but after a reboot, I was able to remove the journal successfully.
2) If you actually run debugfs interactively via 'sudo debugfs /dev/sda1', you can ls and cd around sda1 to see the stuff still there.  For the super paranoid, you can tell debugfs 'rdump home/my_home_directory /media/external_usb_drive/' or whatever to backup the files that are on there just in case.

Again, thanks so much.  You saved my server a reinstall.
:p

---

