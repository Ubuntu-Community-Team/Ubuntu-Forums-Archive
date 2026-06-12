---
title: "Hard drive lost"
date: 2012-12-25
forum: Hardware
---

### Post by ch3at3r on 2012-12-25
I accidentally unmounted one of my hard drives. How can I mount it again?
I cannot enter to Linux anymore so I have to use LinuxLiveCD.  
I tried in livecd "/etc/fstab" /command, but terminal says permission denied...
I have tried different SATA/power cables etc. BIOS does not notice that hard drive anymore.
So how can I mount that hard drive back?


Additional info: I put in few days ago new hard drive and tried to copy files from that afterwards disappeared hard drive to new one. It did it few minutes and then say "cannot move..." After that I canceled it and then hard drive disappeared. I shut down and booted computer and then I can see it again and working. But slow. (That all I did in Windows)

Anyway. Now its totally lost (and me too).

Thanks a lot and I hope you understand.

---

### Post by snowpine on 2012-12-25
The Linux command to mount a drive is "mount" and here is a good how-to: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by ch3at3r on 2012-12-25
> **snowpine said:**
> The Linux command to mount a drive is "mount" and here is a good how-to: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

I get following message:
root@ubuntu:/home/ubuntu# mount /dev/sdb2 /mnt
mount: you must specify the filesystem type

root@ubuntu:/home/ubuntu# mount -t ntfs-3g /dev/sdb2 /mnt
NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


So what I have to do?

---

### Post by snowpine on 2012-12-25
Are you sure /dev/sdb6 is the correct partition?
What about just trying to access the drive through Places in Nautilus file manager?

---

### Post by ch3at3r on 2012-12-25
> **snowpine said:**
> Are you sure /dev/sdb6 is the correct partition?
What about just trying to access the drive through Places in Nautilus file manager?

I am quite sure that its /dev/sdb2 because its size is right.
How do I do that Nautilus thing?
I am not very good in Linux...

---

### Post by snowpine on 2012-12-25
Most file managers (such as Nautilus) have a left "pane" or column where you can select different partitions. Or you can go to the Go menu and choose Computer. 

Please don't edit your old posts with new information, but rather post a new reply with the new information---this will make the conversation easier to follow. 

I'm sorry but I am not a Windows user and not an expert on NTFS.

---

### Post by ch3at3r on 2012-12-25
> **snowpine said:**
> Most file managers (such as Nautilus) have a left "pane" or column where you can select different partitions. Or you can go to the Go menu and choose Computer. 

Please don't edit your old posts with new information, but rather post a new reply with the new information---this will make the conversation easier to follow. 

I'm sorry but I am not a Windows user and not an expert on NTFS.

I cannot see that drive anywhere. Only in terminal...

---

### Post by snowpine on 2012-12-25
I apologize for offering to help, but I am not qualified to troubleshoot NTFS.

---

### Post by Yellow Pasque on 2012-12-26
> I have tried different SATA/power cables etc. BIOS does not notice that hard drive anymore.
Are you sure? I guess the drive could have failed at the same time you unmounted it, but my "coincidence too good to be true" meter is rising off the chart.

Please share:
```
sudo fdisk -l
```

---

### Post by ch3at3r on 2012-12-26
> **Temüjin said:**
> Are you sure? I guess the drive could have failed at the same time you unmounted it, but my "coincidence too good to be true" meter is rising off the chart.

Please share:
```
sudo fdisk -l
```

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f94aa17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  2930274303  1465136128    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00310030

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   245762369   122881153+   7  HPFS/NTFS/exFAT
/dev/sdb2       245764094  1953503999   853869953    f  W95 Ext'd (LBA)
/dev/sdb5       389126493  1953503999   782188753+   7  HPFS/NTFS/exFAT
/dev/sdb6       380530688   389126143     4297728   82  Linux swap / Solaris
/dev/sdb7       245764096   363800575    59018240   83  Linux
/dev/sdb8       363802624   380516351     8356864   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 4006 MB, 4006608896 bytes
39 heads, 39 sectors/track, 5144 cylinders, total 7825408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        3136     7825407     3911136    b  W95 FAT3

---

### Post by ch3at3r on 2012-12-28
How do I mount missing hard drive?
And which one it is from earlier post?
Thanks.

---

### Post by westie457 on 2012-12-28
> /dev/sda1 2048 2930274303 1465136128 7 HPFS/NTFS/[COLOR="Red"]exFAT[/COLOR]

Here you go. the problem is highlighted in red.

'exfat' is a Microsoft only filesystem format. Linux cannot read it.

To look at those partitions with Linux means they have to be re-formatted to something other than exfat.

Use Windows to move any files you want to keep. Then format to NTFS or FAT32 for best results of readability.

---

### Post by Yellow Pasque on 2012-12-28
@westie: it doesn't say the partition is exfat (could be HPFS or NTFS) and i don't think that's the disk the OP is looking for.

I think the OP wants /dev/sdb5 as /dev/sdb2 is an extended/logical partition.

---

### Post by Wim Sturkenboom on 2012-12-28
> **westie457 said:**
> Here you go. the problem is highlighted in red.
It's not; I don't have any issues mounting partitions that are of that type ;) They are formatted as NTFS.

To ch3at3r
1)
/etc/fstab is not a command; it's a file that can be edited (need root permissions) with e.g. gedit **[COLOR="Red"]IF[/COLOR]** you know what you are doing.
2)
To mount, use (similar to what you already used)
```

sudo mount /dev/sdb5 /mnt

```
It should pick up the format / type without problems. You can unmount with
```

umount /dev/sda5

```

---

### Post by snowpine on 2012-12-28
> **ch3at3r said:**
> I am quite sure that its /dev/sdb2 because its size is right.


I am quite sure it is not because /dev/sdb2 is an "extended" partition, which cannot directly hold data.

Here is a guide that will clear up these partitioning basics for you:

[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

---

### Post by ch3at3r on 2012-12-28
> **Wim Sturkenboom said:**
> It's not; I don't have any issues mounting partitions that are of that type ;) They are formatted as NTFS.

To ch3at3r
1)
/etc/fstab is not a command; it's a file that can be edited (need root permissions) with e.g. gedit **[COLOR=Red]IF[/COLOR]** you know what you are doing.
2)
To mount, use (similar to what you already used)
```

sudo mount /dev/sdb5 /mnt

```It should pick up the format / type without problems. You can unmount with
```

umount /dev/sda5

```

After "sudo mount /dev/sdb5 /mnt"
it gives following error message:
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

---

### Post by Wim Sturkenboom on 2012-12-28
> **ch3at3r said:**
> After "sudo mount /dev/sdb5 /mnt"
it gives following error message:
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.I'm not the person to help you with this but what is thge output of the mount command?

```

wim@i3-2120:~$ mount
...
...
/dev/sdb1 on /media/WinXP type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
wim@i3-2120:~$ 

```
I mounted a Windows partition (/dev/sdb1 in this case) and the above output tells me where it is mounted. If it's not mounted, maybe the following command can shed some light on which application is using is (but I'm not sure if it returns anything usefull).
```

lsof | grep /dev/sdb1

```

I can get the same error message if I try to mount a second time
```

wim@i3-2120:~$ sudo mount /dev/sdb1 /mnt
[sudo] password for wim: 
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
wim@i3-2120:~$ 

```

Note:
replace sdb1 by your partition

---

### Post by ch3at3r on 2012-12-28
> **Wim Sturkenboom said:**
> I'm not the person to help you with this but what is thge output of the mount command?



/dev/sdb7 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/morojokulinux/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=morojokulinux)
/dev/sda1 on /media/DA8ED3988ED36C0F type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1 on /media/96F2BBE9F2BBCBAD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5 on /media/6076D7D876D7ACD2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

And after sudo mount /dev/sdb7 /mnt
mount -code gives one additional row: 
/dev/sdb7 on /mnt type ext4 (rw)
But I cannot still see my lost disk...
So is it any of those /dev/sdb -things?

---

### Post by Wim Sturkenboom on 2012-12-29
OK, so they are mounted (and hence the error that you get when you try to mount them).

In a terminal, you can run (example for sdb5)
```

ls /media/6076D7D876D7ACD2

```
to see the files and/or directories on it.

I don't know why you can't find them in the file manager. Can you make a printscreen of the filemanager window (resize the window first so it's not too big for download; left panel is the most important part).

---

### Post by ch3at3r on 2012-12-29
> **Wim Sturkenboom said:**
> OK, so they are mounted (and hence the error that you get when you try to mount them).

In a terminal, you can run (example for sdb5)
```

ls /media/6076D7D876D7ACD2

```to see the files and/or directories on it.

I don't know why you can't find them in the file manager. Can you make a printscreen of the filemanager window (resize the window first so it's not too big for download; left panel is the most important part).

It may be too small? But I added that printscreen.
Its in finnish but I guess you understand it anyway..

---

### Post by Wim Sturkenboom on 2012-12-29
Something is clearly wrong in Nautilus; I don't know why. Below is what I see on a system with a couple of hard disks. Win7 is sda2, WinXP and below in the device section are an old dual boot install of WinXP and Ubuntu and on sdb.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229245&d=1356712092[/IMG]

Did you try the command I gave you?

I suggest that you unmount /dev/sdb5 and mount it on /mnt using the two commands below.
```

sudo umount /dev/sdb5
sudo mount /dev/sdb5 /mnt

```
Next the content of sdb5 should be visible under filesystem -> mnt

PS Next time, please convert your xcf to jpg or png. Not everybody has gimp installed. The PNG I posted here was taken directly using <alt><printscreen> (no need to go through the Gimp ;))

---

### Post by ch3at3r on 2012-12-29
> **Wim Sturkenboom said:**
> Something is clearly wrong in Nautilus; I don't know why. Below is what I see on a system with a couple of hard disks. Win7 is sda2, WinXP and below in the device section are an old dual boot install of WinXP and Ubuntu and on sdb.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229245&d=1356712092[/IMG]

Did you try the command I gave you?

I suggest that you unmount /dev/sdb5 and mount it on /mnt using the two commands below.
```

sudo umount /dev/sdb5
sudo mount /dev/sdb5 /mnt

```Next the content of sdb5 should be visible under filesystem -> mnt

PS Next time, please convert your xcf to jpg or png. Not everybody has gimp installed. The PNG I posted here was taken directly using <alt><printscreen> (no need to go through the Gimp ;))

If I umount  sdb5 my 1. hard drive disappears  from left pane. So the drive I have to nount is some different one.
Is it some of sdb:s or sdc???

---

### Post by Wim Sturkenboom on 2012-12-30
I don't know which one it is ;) You posted the output of the mount command earlier (see below). I have highlighted the three mounts that you can check in a terminal. I can't help you to get them visible in the filemanger if they ain't there, but we can check from the command line what is in them.
> **ch3at3r said:**
> ```
/dev/sdb7 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/morojokulinux/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=morojokulinux)
/dev/sda1 on **[COLOR="Red"]/media/DA8ED3988ED36C0F[/COLOR]** type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1 on **[COLOR="Red"]/media/96F2BBE9F2BBCBAD[/COLOR]** type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5 on **[COLOR="Red"]/media/6076D7D876D7ACD2[/COLOR]** type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

Run the following two commands in a terminal.
```

cd /media/DA8ED3988ED36C0F
ls

```
Report if you get errors; does ls give you what your familiar with from windows?

Repeat for the other two mounts that are marked in red.

If you know a filename, you can run the following command
```

find /media/DA8ED3988ED36C0F -name "thefilename"

```
If you're looking for e.g. Microsoft word documents, you can try
```

find /media/DA8ED3988ED36C0F -name "*.doc*"

```
Again, repeat for the other two mounts.

Once you have found what you're looking for, go back to your output of mount and check which partition it is.

---

### Post by ch3at3r on 2012-12-30
> **Wim Sturkenboom said:**
> I don't know which one it is ;) You posted the output of the mount command earlier (see below). I have highlighted the three mounts that you can check in a terminal. I can't help you to get them visible in the filemanger if they ain't there, but we can check from the command line what is in them.

Run the following two commands in a terminal.
```

cd /media/DA8ED3988ED36C0F
ls

```Report if you get errors; does ls give you what your familiar with from windows?

Repeat for the other two mounts that are marked in red.

If you know a filename, you can run the following command
```

find /media/DA8ED3988ED36C0F -name "thefilename"

```If you're looking for e.g. Microsoft word documents, you can try
```

find /media/DA8ED3988ED36C0F -name "*.doc*"

```Again, repeat for the other two mounts.

Once you have found what you're looking for, go back to your output of mount and check which partition it is.

All those three highlighted hard drives are visible!
/dev/sda has only one partition
/dev/sda1 = 1,5TB E-levy
/dev/sdb has two partitions
/dev/sdb1 = 125GB C-drive (inc. Windows 7 64bit and Linux Ubuntu 12.04)
/dev/sdb5 =  800GB F-drive

So how can I know what is that missing 1TB (only one partition) drive?

---

### Post by Wim Sturkenboom on 2012-12-30
From your fdisk output (quoted below), you don't have a 1TB (one partition) drive.
> **ch3at3r said:**
> 
```

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f94aa17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  2930274303  1465136128    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00310030

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   245762369   122881153+   7  HPFS/NTFS/exFAT
/dev/sdb2       245764094  1953503999   853869953    f  W95 Ext'd (LBA)
/dev/sdb5       389126493  1953503999   782188753+   7  HPFS/NTFS/exFAT
/dev/sdb6       380530688   389126143     4297728   82  Linux swap / Solaris
/dev/sdb7       245764096   363800575    59018240   83  Linux
/dev/sdb8       363802624   380516351     8356864   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 4006 MB, 4006608896 bytes
39 heads, 39 sectors/track, 5144 cylinders, total 7825408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        3136     7825407     3911136    b  W95 FAT3

```


You have a 1.5TB drive with one partition (/dev/sda1).

You have a 1TB drive with a primary partition (/dev/sdb1) and an extended partition (/dev/sdb2). This extented partition contains the following logical partitions
[LIST]
[*]/dev/sdb5 (some windows related stuff)
[*]/dev/sdb6 and /dev/sdb8 (linux swap)
[*]/dev/sdb7 (your linux install)
[/LIST]

And you have a 4GB disk with one partition (/dev/sdc1) which I assume is a memory stick.

How many drives do you have in your system?

---

### Post by ch3at3r on 2012-12-30
> **Wim Sturkenboom said:**
> From your fdisk output (quoted below), you don't have a 1TB (one partition) drive.


You have a 1.5TB drive with one partition (/dev/sda1).

You have a 1TB drive with a primary partition (/dev/sdb1) and an extended partition (/dev/sdb2). This extented partition contains the following logical partitions
[LIST]
[*]/dev/sdb5 (some windows related stuff)
[*]/dev/sdb6 and /dev/sdb8 (linux swap)
[*]/dev/sdb7 (your linux install)
[/LIST]

And you have a 4GB disk with one partition (/dev/sdc1) which I assume is a memory stick.

How many drives do you have in your system?

I have three (3) drives.
1x 1,5TB
2x 1TB (the other one is missing, but plugged)

---

### Post by Wim Sturkenboom on 2012-12-30
Aha, must have missed that somewhere in your earlier posts if it was mentioned. It's indeed missing ;) Is it seen in the BIOS? Is it seen in dmesg. Below for my 3 disks
```

wim@i3-2120:~$ **[COLOR="Red"]dmesg |grep sd[/COLOR]**
[    1.316019] sd 0:0:0:0: [[COLOR="Red"]sda[/COLOR]] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.316020] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.316046] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.316127] sd 0:0:0:0: [sda] Write Protect is off
[    1.316134] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.316190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.322965] sd 1:0:0:0: [[COLOR="Red"]sdb[/COLOR]] 490234752 512-byte logical blocks: (251 GB/233 GiB)
[    1.322997] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.323040] sd 1:0:0:0: [sdb] Write Protect is off
[    1.323042] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.323076] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.338021] sd 4:0:0:0: [[COLOR="Red"]sdc[/COLOR]] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.338042] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    1.338052] sd 4:0:0:0: [sdc] Write Protect is off
[    1.338054] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.338075] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.369129]  sdc: sdc1
[    1.369300] sd 4:0:0:0: [sdc] Attached SCSI disk
[    1.383113]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.383594] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.410972]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 sdb8 sdb9 >
[    1.411502] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.886613] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    9.721616] Adding 8000508k swap on /dev/sda3.  Priority:-1 extents:1 across:8000508k 
[    9.729632] Adding 4179964k swap on /dev/sdb8.  Priority:-2 extents:1 across:4179964k 
[   10.659000] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   10.949924] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   12.111233] EXT3-fs (sdc1): using internal journal
[   12.111238] EXT3-fs (sdc1): mounted filesystem with ordered data mode
[   12.214718] type=1400 audit(1356877477.670:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1086 comm="apparmor_parser"

```Check if there is a reference to sdc (not being your memory stick).

---

### Post by ch3at3r on 2012-12-30
> **Wim Sturkenboom said:**
> Aha, must have missed that somewhere in your earlier posts if it was mentioned. It's indeed missing ;) Is it seen in the BIOS? Is it seen in dmesg. Below for my 3 disks
```

wim@i3-2120:~$ **[COLOR=Red]dmesg |grep sd[/COLOR]**
[    1.316019] sd 0:0:0:0: [[COLOR=Red]sda[/COLOR]] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.316020] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.316046] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.316127] sd 0:0:0:0: [sda] Write Protect is off
[    1.316134] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.316190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.322965] sd 1:0:0:0: [[COLOR=Red]sdb[/COLOR]] 490234752 512-byte logical blocks: (251 GB/233 GiB)
[    1.322997] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.323040] sd 1:0:0:0: [sdb] Write Protect is off
[    1.323042] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.323076] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.338021] sd 4:0:0:0: [[COLOR=Red]sdc[/COLOR]] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.338042] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    1.338052] sd 4:0:0:0: [sdc] Write Protect is off
[    1.338054] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.338075] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.369129]  sdc: sdc1
[    1.369300] sd 4:0:0:0: [sdc] Attached SCSI disk
[    1.383113]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.383594] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.410972]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 sdb8 sdb9 >
[    1.411502] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.886613] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    9.721616] Adding 8000508k swap on /dev/sda3.  Priority:-1 extents:1 across:8000508k 
[    9.729632] Adding 4179964k swap on /dev/sdb8.  Priority:-2 extents:1 across:4179964k 
[   10.659000] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   10.949924] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   12.111233] EXT3-fs (sdc1): using internal journal
[   12.111238] EXT3-fs (sdc1): mounted filesystem with ordered data mode
[   12.214718] type=1400 audit(1356877477.670:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1086 comm="apparmor_parser"

```Check if there is a reference to sdc (not being your memory stick).

Cannot see in BIOS. dmesg shows only sda and sdb:
> dmesg |grep sd
[    2.045308] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.045368] sd 1:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.045541] sd 1:0:0:0: [sda] Write Protect is off
[    2.045543] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.045549] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.045566] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.045592] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.045625] sd 2:0:0:0: [sdb] Write Protect is off
[    2.045627] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.045641] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.058973]  sda: sda1
[    2.059506] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.088206]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 sdb8 >
[    2.088798] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.556061] EXT4-fs (sdb7): mounted filesystem with ordered data mode. Opts: (null)
[   70.299777] Adding 8356860k swap on /dev/sdb8.  Priority:-1 extents:1 across:8356860k 
[   70.714849] EXT4-fs (sdb7): re-mounted. Opts: errors=remount-ro
[   87.544872] type=1400 audit(1356939627.840:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1089 comm="apparmor_parser"
[   89.026845] EXT4-fs (sdb7): re-mounted. Opts: errors=remount-ro,commit=0
[   90.398726] EXT4-fs (sdb7): re-mounted. Opts: errors=remount-ro,commit=0


---

