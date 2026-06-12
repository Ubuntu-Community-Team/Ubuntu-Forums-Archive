---
title: "Can't copy files to external hardrive"
date: 2009-10-12
forum: Hardware
---

### Post by Radissthor on 2009-10-12
Hello everyone,

I have Ubuntu 9.04 in a Dell Inspiron 1525. I have a cirago external hardrive Cirago CST1500. It came with a drivers CD, but the CD only has options for Windows 9x, Windows XP-Vista and it has a text file that says For MAC OS and Linux. The text says the following:

Thank you for purchasing a Cirago storage product for your Macintosh or Linux system.  For your convenience, we have listed a few popular web-site where you can find tools and utilities for all your storage needs.\
\
\pard\pardeftab720\ri720\ql\qnatural
\cf0 Linux:\
	[www.linuxappfinder.com\](www.linuxappfinder.com\)
	[www.sourceforge.net\](www.sourceforge.net\)

I found nothing on those websites. I'm a newbie on Ubuntu, so I would greatly appreciate some help in this. :)

By the way, the problem is that I can't seem to be able to modify things in the hardrive, though I can read it and copy files from it to the computer. But I can't copy files into the external device, nor can I modify files that are contained in it. When I try to copy files, it says:

"The destination is read-only"

---

### Post by Radissthor on 2009-10-13
Well, 15 hours without a reply, si I'm asking again if anyone can help me with this. 
Many thanks.

---

### Post by arrange on 2009-10-13
Disconnect the drive, wait a few seconds, and connect it back again. Then open the [Terminal](https://help.ubuntu.com/community/GnomeTerminal) and [copy](https://help.ubuntu.com/community/UsingTheTerminal#Pasting%20in%20commands) these commands into it```
dmesg | tail -20
lsusb
mount
sudo fdisk -l
```Then copy the output here (log, usb devices list, partitions list).

---

### Post by rb0171610 on 2009-10-13
> **Radissthor said:**
> Hello everyone,

I have Ubuntu 9.04 in a Dell Inspiron 1525. I have a cirago external hardrive Cirago CST1500. It came with a drivers CD, but the CD only has options for Windows 9x, Windows XP-Vista and it has a text file that says For MAC OS and Linux. The text says the following:

Thank you for purchasing a Cirago storage product for your Macintosh or Linux system.  For your convenience, we have listed a few popular web-site where you can find tools and utilities for all your storage needs.\
\
\pard\pardeftab720\ri720\ql\qnatural
\cf0 Linux:\
    [www.linuxappfinder.com\]("http://www.linuxappfinder.com%5C")
    [www.sourceforge.net\]("http://www.sourceforge.net%5C")

I found nothing on those websites. I'm a newbie on Ubuntu, so I would greatly appreciate some help in this. :)

By the way, the problem is that I can't seem to be able to modify things in the hardrive, though I can read it and copy files from it to the computer. But I can't copy files into the external device, nor can I modify files that are contained in it. When I try to copy files, it says:

"The destination is read-only"
Obviously, when the hard drive is being mounted in Linux, it is being mounted Read-Only.  At first glance, it appears that this drive connects using a USB interface and does not require an external power source.  I cannot find a spec sheet for this particular model.  There are a couple of things to consider.  Will you be needing to use this external hard drive with more than one computer?  If so, will all of those computers be running Linux?  Do you need to use this external drive with Windows computers? 
 If you only need to access this drive from Linux computers, you are free to backup the data and reformat it using a Linux compatible file system such as ext3 or reiserfs.  Windows computers cannot natively read Linux file systems.   You can then mount the drive in Linux with read/write permissions rather than read-only.  
If this drive is formatted with the FAT file system, it is readable in Linux and Windows and should be able to be mounted with read/write permissions rather than read-only.
If this drive has been formatted using NTFS, the default file system used by Windows XP and Vista, it is usually mounted read-only in Linux machines.  There is an NTFS driver for Linux that will allow you to write to an NTFS partition; however, I have never used it.  Previously this driver was not stable.  Whether or not this driver currently is able to freely write to NTFS partitions without causing possible data loss, I do not know as I only need to mount my Windows NTFS partitions as read-only.  Maybe someone else would like shed light on the subject.
That being said, there sometimes is some Windows software installed on a small partition of external hard drives that allows a user to restore or back up data with the click of a mouse from within Windows.  If this hard drive has this software, and you intend to use it, you obviously would not want to overwrite the partitions with a Linux file system.
So, if the hard drive is formatted with NTFS and shared with Windows computers, you will probably only be mounting it with read-only permissions in Linux.  If it is formatted with a FAT file system, you should be able to mount it with read/write permissions in both Linux and Windows.  If you are free to format it with a Linux file system, then Windows computers will not natively have the capabilities needed to read and write to this partition.  If there is software installed on the hard drive that interfaces with Windows, you would not be able to use this software if you overwrite the partition where the software is installed.
I hope this helps.  Good Luck.

---

### Post by Radissthor on 2009-10-13
Ok, so when I typed 
dmesg | tail -20

it showed:

[  265.707962] FAT: Filesystem panic (dev sdb1)
[  265.707970]     invalid access to FAT (entry 0xd49d93c5)
[  265.733282] FAT: Filesystem panic (dev sdb1)
[  265.733289]     invalid access to FAT (entry 0xd49d93c5)
[  265.735260] FAT: Filesystem panic (dev sdb1)
[  265.735268]     invalid access to FAT (entry 0xd49d93c5)
[  265.736322] FAT: Filesystem panic (dev sdb1)
[  265.736329]     invalid access to FAT (entry 0xf81339b7)
[  265.771951] attempt to access beyond end of device
[  265.771962] sdb1: rw=0, want=88454573220, limit=488392002
[  265.784181] FAT: Filesystem panic (dev sdb1)
[  265.784189]     invalid access to FAT (entry 0xd49d93c5)
[  265.793135] attempt to access beyond end of device
[  265.793144] sdb1: rw=0, want=88454573220, limit=488392002
[  265.793843] FAT: Filesystem panic (dev sdb1)
[  265.793851]     invalid access to FAT (entry 0xd49d93c5)
[  265.798084] FAT: Filesystem panic (dev sdb1)
[  265.798092]     invalid access to FAT (entry 0xf81339b7)
[  265.798533] FAT: Filesystem panic (dev sdb1)
[  265.798537]     invalid access to FAT (entry 0xf81339b7)

For 
lsusb
it showed:
Bus 002 Device 003: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

For
mount
it showed:
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hernan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hernan)
/dev/sdb1 on /media/SWISNIFE1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

and for 
sudo fdisk -l
it showed (after asking for the password)
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1c0e46a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73a58251

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32



rb0171610, I appreciate the advice, but I'm afraid you're talking way out of my league. I'm a total newbie at Linux (and computers in general) but thanks anyway!

So, what does all this mean? anyone?

---

### Post by rb0171610 on 2009-10-13
> **Radissthor said:**
> Ok, so when I typed 
dmesg | tail -20

it showed:

[  265.707962] FAT: Filesystem panic (dev sdb1)
[  265.707970]     invalid access to FAT (entry 0xd49d93c5)
[  265.733282] FAT: Filesystem panic (dev sdb1)
[  265.733289]     invalid access to FAT (entry 0xd49d93c5)
[  265.735260] FAT: Filesystem panic (dev sdb1)
[  265.735268]     invalid access to FAT (entry 0xd49d93c5)
[  265.736322] FAT: Filesystem panic (dev sdb1)
[  265.736329]     invalid access to FAT (entry 0xf81339b7)
[  265.771951] attempt to access beyond end of device
[  265.771962] sdb1: rw=0, want=88454573220, limit=488392002
[  265.784181] FAT: Filesystem panic (dev sdb1)
[  265.784189]     invalid access to FAT (entry 0xd49d93c5)
[  265.793135] attempt to access beyond end of device
[  265.793144] sdb1: rw=0, want=88454573220, limit=488392002
[  265.793843] FAT: Filesystem panic (dev sdb1)
[  265.793851]     invalid access to FAT (entry 0xd49d93c5)
[  265.798084] FAT: Filesystem panic (dev sdb1)
[  265.798092]     invalid access to FAT (entry 0xf81339b7)
[  265.798533] FAT: Filesystem panic (dev sdb1)
[  265.798537]     invalid access to FAT (entry 0xf81339b7)

For 
lsusb
it showed:
Bus 002 Device 003: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

For
mount
it showed:
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hernan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hernan)
/dev/sdb1 on /media/SWISNIFE1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

and for 
sudo fdisk -l
it showed (after asking for the password)
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1c0e46a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73a58251

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32



rb0171610, I appreciate the advice, but I'm afraid you're talking way out of my league. I'm a total newbie at Linux (and computers in general) but thanks anyway!

So, what does all this mean? anyone?
It means that you did not answer any of the questions I gave you.  Do you have important files on this drive?  Can you back them up somewhere?  Do you need to access this drive from a Windows Computer? Or only Linux?  


And while I understand that it may not make a lot of sense to  you now, this is a public forum and when people search Google for the same problem you are having, it might actually bring them right here to this page.  

If you could kindly answer my questions, I may be able to help you make good use of your external hard drive.

The most likely cause is that you unplugged the drive while it was writing files and the file system needs to be fixed.  You can run a disk check in Windows to fix it. 

If you can answer the questions I posed to you it will help.

Thanks.

---

### Post by Radissthor on 2009-10-13
Ok Rob, I guess you're right. I just freaked put when I saw all that text, sorry :oops:

I'll be mainly using this hardrive in Ubuntu, but I'd also like to work in Windows, since I may want to move files from my computer to others, specially at work, where everyone uses Windows... 
I do have important files... they are all the files I had in Windows and that I backed up when I changed to Ubuntu a few days ago. So, obviosly, the 
hardrive does have read and write permissions in Windows...

Did I answer the questions? I'll be checking your reply. Thanks for being so patience :D

---

### Post by rb0171610 on 2009-10-13
> **Radissthor said:**
> Ok Rob, I guess you're right. I just freaked put when I saw all that text, sorry :oops:

I'll be mainly using this hardrive in Ubuntu, but I'd also like to work in Windows, since I may want to move files from my computer to others, specially at work, where everyone uses Windows... 
I do have important files... they are all the files I had in Windows and that I backed up when I changed to Ubuntu a few days ago. So, obviosly, the 
hardrive does have read and write permissions in Windows...

Did I answer the questions? I'll be checking your reply. Thanks for being so patience :D

The first thing you should do is backup everything on this hard drive to another computer.  :)

Secondly, do you have access to a Windows computer right now? Or only Ubuntu?

---

### Post by Radissthor on 2009-10-13
Yes, I could borrow my sister's laptop. It has windows vista, or the ones where I work, they have XP

---

### Post by rb0171610 on 2009-10-13
> **Radissthor said:**
> Ok, so when I typed 
dmesg | tail -20

it showed:

[  265.707962] FAT: Filesystem panic (dev sdb1)
[  265.707970]     invalid access to FAT (entry 0xd49d93c5)
[  265.733282] FAT: Filesystem panic (dev sdb1)
[  265.733289]     invalid access to FAT (entry 0xd49d93c5)
[  265.735260] FAT: Filesystem panic (dev sdb1)
[  265.735268]     invalid access to FAT (entry 0xd49d93c5)
[  265.736322] FAT: Filesystem panic (dev sdb1)
[  265.736329]     invalid access to FAT (entry 0xf81339b7)
[  265.771951] attempt to access beyond end of device
[  265.771962] sdb1: rw=0, want=88454573220, limit=488392002
[  265.784181] FAT: Filesystem panic (dev sdb1)
[  265.784189]     invalid access to FAT (entry 0xd49d93c5)
[  265.793135] attempt to access beyond end of device
[  265.793144] sdb1: rw=0, want=88454573220, limit=488392002
[  265.793843] FAT: Filesystem panic (dev sdb1)
[  265.793851]     invalid access to FAT (entry 0xd49d93c5)
[  265.798084] FAT: Filesystem panic (dev sdb1)
[  265.798092]     invalid access to FAT (entry 0xf81339b7)
[  265.798533] FAT: Filesystem panic (dev sdb1)
[  265.798537]     invalid access to FAT (entry 0xf81339b7)

For 
lsusb
it showed:
Bus 002 Device 003: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

For
mount
it showed:
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hernan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hernan)
/dev/sdb1 on /media/SWISNIFE1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

and for 
sudo fdisk -l
it showed (after asking for the password)
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1c0e46a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73a58251

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32



rb0171610, I appreciate the advice, but I'm afraid you're talking way out of my league. I'm a total newbie at Linux (and computers in general) but thanks anyway!

So,what does all this mean? anyone?
Meanwhile, to answer your question, "What does it all mean?" :
You ran the dmesg command.
**dmesg** (for "**d**isplay **mes**sa**g**e") is a command that prints the message buffer of the kernel.  What does that mean? It basically prints the system messages that you cannot see.  When you typed: 
```
dmesg | tail -20
```you asked to see the last 20 (tail end) of the system messages. 
Which is what it returned to you -- 20 lines.  

In these system messages you can see the relevant keywords **FAT**, **Filesystem**, **dev** **sdb1**,  and **invalid access** to FAT:

[  265.707962] FAT: Filesystem panic (dev sdb1)
[  265.707970]     invalid access to FAT (entry 0xd49d93c5)

Do you see them?  FAT stands for **F**ile **A**llocation** T**able.  FAT is a type of file system or way of storing and organizing files and information on a hard drive.  Windows98 used a version of this called FAT32.  In Windows XP, FAT32 could still be used, but Microsoft developed a better file system called NTFS or New Technology File System.  This is the standard Windows File system in use today, but the FAT file system is still used on most external hard drives and USB sticks.
  
When you used the lsusb command you were asking your terminal to list all of the USB devices that are plugged into your computer. Get it, **L**i**S**t **USB**?  There is nothing of major significance in the output.

The mount command is used to mount filesystems.  If you type *man mount* at the terminal it will show you the manual for the mount command. In this manual you will see: 
[I]
mount - mount a file system[/I]

[I]DESCRIPTION
       All  files  accessible  in  a Unix system are arranged in one big tree, the file hierarchy, rooted at /. These files can be spread out over several devices. The mount command serves to attach the file  system found on some device to the big file tree. Conversely, the umount command will detach it again.
[/I]
When you type mount by itself with -**l**, it will **l**ist all of the file systems that are currently **mount**ed in your computer.  A lot of lines were returned, but the one that we are looking for is the last one:

*/dev/sdb1 on /media/SWISNIFE1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)*
 
The first part, /dev/sdb1 is the actual device as it is referred to by the computer.  While this may not mean anything to you, if you will look at the very beginning of this post at the output given to you by the dmesg command, you will also notice that it contains a reference to the **dev**ice **sdb1**.  The other important thing the mount output tells us are the words *type vfat*.  The file system type for **sdb1** is v**fat**.  The portion in parenthesis tells us something as well.  The device is mounted with **r**ead and **w**rite permissions -- meaning you should be able to **r**ead files from and **w**rite files to this device.  How do we know that?  You guessed it -- the first two letters **rw** (**r**ead/**w**rite.)  Everything else would be insignificant to you at this point, but I can tell by experience there is nothing out of the ordinary that would be causing your problem.  Trust me.  Do you trust me? ;)

Finally, the last command you typed was fdisk.  If you were to type **man** fdisk, you could see the **man**ual for this command. It says:

[I]fdisk - Partition table manipulator for Linux

DESCRIPTION
       Hard  disks can be divided into one or more logical disks called partitions.  This division is described in the partition table found in sector 0 of the disk.[/I]

When you type the command *fdisk -**l***, you are asking it to **l**ist information about all of the hard disks in or attached to your computer.  The part that is significant to us right now is:

*Disk /dev/sdb: 250.0 GB  *blah blah blah . . .

You see the **dev**ice that your computer calls **sdb** which has 250GB of space.  

So, for right now we know several things.  Your computer can see the hard drive (there is a **dev**ice name for it), it has a **FAT** file system, and it is mounted with **r**ead **w**rite permissions.  Everything would be fine, except for one thing.  dmesg tells us there are problems writing to your external hard drive :  **FAT**: **Filesystem** panic (**dev** **sdb1**) **invalid access** to [B]FAT 
[/B]The problem is likely that the filesystem is corrupt. 


So what can you do?  A couple of things.  First, copy everything that is on the drive to a folder on your computer. After it is backed up, someone here can assist you with either: 
A) reformatting the drive in Windows or Linux, your choice 
**OR**
B) trying to fix the file system from a Windows computer.

If you try both of these and you still have problems, then the hard drive is likely damaged.  At that point you can toss it, or try to take it back to where you purchased it for a replacement or a refund.

Welcome to Linux, Happy Reading, and Good Luck!

---

### Post by rb0171610 on 2009-10-14
> **Radissthor said:**
> Yes, I could borrow my sister's laptop. It has windows vista, or the ones where I work, they have XP
You first step is to copy everything from the hard drive to your Linux computer, your sister's computer, or both.
When you are finished, you should connect the hard drive to your sister's computer.  At this point you can use the following tutorial:

[http://www.windows-help-central.com/windows-vista-chkdsk.html](http://www.windows-help-central.com/windows-vista-chkdsk.html)

to try and fix the disk.  The tutorial has easy to follow instructions with pictures. (YAY pictures!!!) If you have questions, post here and I or someone else will help you. 
This should (keep your fingers crossed) fix your problem.  If not, your next step will be to reformat the disk.  This will wipe it clean and hopefully get it back to the way it was when you purchased it.

You do not have to do the disk check first.  You can opt to wipe the hard drive and reformat it.  If you have backed up your data, this may be the quickest solution. It is entirely up to you.  The disk check will try to fix it and keep the data intact, the reformatting will wipe it clean.

Let us know if you need help.

Good Luck.

---

### Post by Radissthor on 2009-10-14
Wow Rob many thanks man, that was the most comprehensive explanation I have ever read on commands. I really appreciate the time you took to help. 

I'll be checking the windows solution and post back my experience. 
Best Regards,

---

### Post by Radissthor on 2009-10-14
It worked! I followed the tutorial you gave me on disk check on vista. It took like 6 minutes. It found the errors and repaired them. Then, I mounted it and the read/write permisions were there!

Thanks for all the help! Viva Ubuntu!:guitar:

---

