---
title: "The Mystery of the Lost Partition"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Jesdisciple on 2009-06-16
While I was [working off the Live CD]("http://ubuntuforums.org/showthread.php?t=1187234"), one of my partitions mysteriously disappeared.  It's /dev/sda5 and was mounted at /home.  I wonder what I need to do to re-mount it?

Many thanks.

```
$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00025eb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2755    22129506   83  Linux
/dev/sda2            2756        5510    22129537+  83  Linux
/dev/sda3            5511        8174    21398580   83  Linux
/dev/sda4            8175        9729    12490537+   5  Extended
/dev/sda5            8175        9480    10490413+  83  Linux
/dev/sda6            9481        9597      939771    b  W95 FAT32
/dev/sda7            9598        9729     1060258+  82  Linux swap / Solaris
$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="233e0e09-aa16-4335-a004-50834698130c" TYPE="ext4" 
/dev/sda2: UUID="c598cf67-264d-4d78-b90d-5f02a1135797" TYPE="ext4" 
/dev/sda3: LABEL="Windows" UUID="8a584d98-10ea-4725-9b15-3a7afa9e6efc" TYPE="ext4" 
/dev/sda5: UUID="8f4c89b8-6e85-43dc-8da4-565c144a73ef" TYPE="ext4" 
/dev/sda6: UUID="5393-38DF" TYPE="vfat" 
/dev/sda7: UUID="2a22f359-908e-43df-9fb6-d8fdb10daaa0" TYPE="swap"
```

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /media/main was on /dev/sda1 during installation
UUID=233e0e09-aa16-4335-a004-50834698130c /media/main     ext4    relatime        0       2
# / was on /dev/sda2 during installation
UUID=c598cf67-264d-4d78-b90d-5f02a1135797 /               ext4    relatime,errors=remount-ro 0       1
# /media/windows was on /dev/sda3 during installation
UUID=8a584d98-10ea-4725-9b15-3a7afa9e6efc /media/windows  ext4    relatime        0       2
# /home was on /dev/sda5 during installation
UUID=8f4c89b8-6e85-43dc-8da4-565c144a73ef /home           ext4    relatime        0       2
# /media/share was on /dev/sda6 during installation
UUID=5393-38DF  /media/share    vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda7 during installation
UUID=2a22f359-908e-43df-9fb6-d8fdb10daaa0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by dstew on 2009-06-16
Do you mean that your Ubuntu hard disk system no longer can mount /dev/sda5? The partition still exists, I see it on your fdisk output. The UUID seems OK. The fstab entry seems OK too. Did you try manually mounting it?```
sudo mount /dev/sda5 /home
```If so, do you get an error?

EDIT: I notice that the pass number (sixth field) in the entry for /dev/sda6 is 1. Probably should make it 0, or 2. I don't know if this is causing a problem, but usually only the root filesystem uses the pass number 1.

---

### Post by Jesdisciple on 2009-06-16
```
$ sudo mount /dev/sda5 /home
[sudo] password for coder: 
mount: /dev/sda5 already mounted or /home busy
mount: according to mtab, /dev/sda5 is already mounted on /home
```

That figures.  There's been a different explanation for just about every problem I've had in the last few weeks.  So I'll go back to the problem itself...  I had used this installation and account extensively before the ordeal described in the linked thread.  I really don't think the lightning had anything to do with this part as everything works fine.

Here's what I'm sure about...  I installed eSvn and Debian's reportbug on this account, and I had to reinstall them.  Then I looked at the profiles for my two main installations and was surprised at how empty they were.  I know programs don't normally install to /home, so I obviously jumped the gun.  However, I'm pretty sure something happened to this account - not the other one because I haven't used it much yet.

... =\ ...  I know I'm being pretty vague, but do you have any idea what the Live CD might have had to do with this?  That's the only "suspect" I have.

---

### Post by dstew on 2009-06-16
Usually, the Live CD is well-behaved, and will not alter your hard disk partitions unless you deliberately mount them to the Live CD system. If you mount them, the files can be manipulated.

If you install programs onto a Live CD system, the programs will disappear when you shut it down.

Maybe I'm not sure exactly what you are asking.

---

### Post by Jesdisciple on 2009-06-16
I never explicitly mounted anything to the Live CD, but I manipulated and uploaded several files after finding the drive.

I don't know that I'm asking anything in particular; it's kind of an open-ended question.  Bah, I guess I can't give a description of the problem good enough to be of any use.  So I'll probably either run into more trouble and ask again, or (more likely, I suppose) it'll just blow over.

Thanks.

---

