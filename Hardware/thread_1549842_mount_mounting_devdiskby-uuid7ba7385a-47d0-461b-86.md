---
title: "mount: mounting /dev/disk/by-uuid/7ba7385a-47d0-461b-86cf-7157206a2e38 on /root"
date: 2010-08-10
forum: Hardware
---

### Post by l0uismustdie on 2010-08-10
I am running Ubuntu 10.04 on my Gateway laptop (AMD 64 Processor).  Yesterday my computer froze and after a rebooted I was faced with this screen:

```

mount: mounting /dev/disk/by-uuid/7ba7385a-47d0-461b-86cf-7157206a2e38 on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init = bootarg

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) Enter 'help' for a list of built-in comands.

(initramfs)

```Thanks in advance for any help you can offer
Josh

---

### Post by l0uismustdie on 2010-08-11
Anyone out there have any ideas about this one??

---

### Post by Pbethe on 2010-08-11
> **l0uismustdie said:**
> Anyone out there have any ideas about this one??

It looks like whatever failure your machine had messed up your file system.  Try booting from a live CD and see if it detects your disk(s).

---

### Post by l0uismustdie on 2010-08-13
Sorry for the delay.  Booting for my USB key has allowed me access to the machine but has not mounted my filesystem.  I have tried to mount my HD in the following ways (in addition to just using "mount volume" in disk utility":
```

ubuntu@ubuntu:/media$ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
ubuntu@ubuntu:/media$ sudo mount -t ext4 /dev/sda1 /mnt
Cmount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```I will also post the output of sudo fdisk -l:
```

ubuntu@ubuntu:/media$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e4d99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9403    75527168   83  Linux
/dev/sda2            9403        9730     2621441    5  Extended
/dev/sda5            9403        9730     2621440   82  Linux swap / Solaris

Disk /dev/sdb: 1058 MB, 1058275328 bytes
33 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2089

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1010     1033199    c  W95 FAT32 (LBA)

```and if it will help here is /etc/fstab:
```

ubuntu@ubuntu:/media$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```and lastly here is sudo blkid:
```

ubuntu@ubuntu:/media$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7ba7385a-47d0-461b-86cf-7157206a2e38" TYPE="ext4" 
/dev/sda5: UUID="45e1053b-e1ac-44f1-8043-8844e93edef9" TYPE="swap" 
/dev/sdb1: UUID="63CB-9014" TYPE="vfat" 

```Thanks to anyone out there who can help on this one.

---

### Post by Pbethe on 2010-08-13
Did you try 
dmesg | tail
after the failed mount commands?  For that matter, it might be worthwhile to capture all of the output of dmesg after trying mount.

---

### Post by MIH1406 on 2010-08-14
I have the same problem, I cannot boot normally nor in recovery mode. I get this message:
```

mount: mounting /dev/disk/by-uuid/f26531dc-0c28-4b8b-84fa-8f0acb615da6 on /root
failed: invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

Here is my **"fdisk -l"** result:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4dff386d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6529    52443168+   7  HPFS/NTFS
/dev/sda2            6530       30402   191753217    5  Extended
/dev/sda5            6530       29779   186750976   83  Linux
/dev/sda6           29779       30402     5001216   82  Linux swap / Solaris

```

And here is my **"cat /etc/fstab"** result;
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

```

And my **"blkid"** result:
```

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2E048AD8048AA287" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sda5: UUID="f26531dc-0c28-4b8b-84fa-8f0acb615da6" TYPE="ext4" 
/dev/sda6: UUID="ccbf4c04-096f-434b-a977-cd3d205f6617" TYPE="swap" 

```

And finally, my **"dmesg | tail"** result:
```

[  950.428255] VFS: busy inodes on changed media or resized disk sr0
[  950.428446] VFS: busy inodes on changed media or resized disk sr0
[  952.429765] VFS: busy inodes on changed media or resized disk sr0
[  952.429962] VFS: busy inodes on changed media or resized disk sr0
[  954.430278] VFS: busy inodes on changed media or resized disk sr0
[  954.430475] VFS: busy inodes on changed media or resized disk sr0
[  956.429816] VFS: busy inodes on changed media or resized disk sr0
[  956.430013] VFS: busy inodes on changed media or resized disk sr0
[  958.430284] VFS: busy inodes on changed media or resized disk sr0
[  958.430487] VFS: busy inodes on changed media or resized disk sr0

```

---

### Post by MIH1406 on 2010-08-14
I tried to mount it using live CD and got this message:
```

Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by IcarusR on 2010-08-14
Boot from cd & in a terminal run..

```
fsck -f /dev/your-drive
```

Change "/your-partition" for your hdd partition.

---

### Post by falisco on 2010-08-17
Hello to everyone in this forum, this is my first post and, please, sorry for my poor english. 

I've been using ubuntu for the last two years but I am a very "basic" user. This week I installed ubuntu in an old 6 

years computer and all went fine. After 5 o 6 reboots the following appears on the screen:

mount: mounting /dev/disk/by-uuid/06d7da4c-0572-4374-be18-80a975561bdd on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/def failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(Initramfs)

I've tried installing Xubuntu 8.10, Ubuntu 9.10 and finally Xubuntu 10.04 and all of them went fine during the installation but also with all of them happened the same after 3-6 reboots.

If I boot with an ubuntu LiveCD, and use disk verification option of gparted, then it boots fine from the hard disk, 

but after 3-6 reboots it fails again with the same message and I have to boot with the LiveCD again to solve it.

I suppose the hard disk is not damaged because this computer has been used for the last 6 years with windows xp every day with no problems.

I've been looking for a solution to this problem in google but I haven't found anything that fixes this error definitely. 

Thank you in advance.

---

### Post by Pbethe on 2010-08-18
> **IcarusR said:**
> Boot from cd & in a terminal run..

```
fsck -f /dev/your-drive
```

Change "/your-partition" for your hdd partition.


In other words, the OP would enter this:

```
fsck -f /dev/sda1
```

If you linux partition is sda5, then

```
fsck -f /dev/sda5
```

Has anyone been able to try this?

---

### Post by l0uismustdie on 2010-08-20
Yeah sorry for the delay.  Hers is the result:
```

root@ubuntu:/home/ubuntu# fsck -f /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1: recovering journal
Error reading block 9475384 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Clearing orphaned inode 131394 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 131380 (uid=1000, gid=1000, mode=0100600, size=400)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 660273
Connect to /lost+found<y>? yes

Inode 660273 ref count is 2, should be 1.  Fix<y>? yes

Pass 5: Checking group summary information
Block bitmap differences:  +15898788
Fix<y>? yes

Free blocks count wrong for group #485 (29222, counted=29221).
Fix<y>? yes

Free blocks count wrong (17455475, counted=17455474).
Fix<y>? yes

Inode bitmap differences:  +660273
Fix<y>? yes

Free inodes count wrong for group #80 (229, counted=228).
Fix<y>? yes

Free inodes count wrong (4553090, counted=4553089).
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 173695/4726784 files (0.2% non-contiguous), 1426318/18881792 blocks

```

Upon reboot was able to boot WITHOUT usb key.  Looks like that solved the problem.  What could have caused this and how can I prevent something like this in the future?  Thanks so much for your reply.

---

### Post by yielder on 2011-11-12
This is what I get when I follow the above steps.
> 
root@ubuntu:~# fsck -f /dev/sda1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1Suggestions greatly appreciated.

Added: I solved the problem.  See [http://ubuntuforums.org/showpost.php?p=11449854&postcount=29](http://ubuntuforums.org/showpost.php?p=11449854&postcount=29)

---

### Post by laziotunisia on 2012-12-28
> **Pbethe said:**
> In other words, the OP would enter this:

```
fsck -f /dev/sda1
```

If you linux partition is sda5, then

```
fsck -f /dev/sda5
```

Has anyone been able to try this?

hi
i had same problem
i try this with ubuntu 12 (i had older version) 
i fixed all problem 
reboot without live CD all ok
many thanks

---

### Post by howefield on 2012-12-28
Old thread closed.

---

