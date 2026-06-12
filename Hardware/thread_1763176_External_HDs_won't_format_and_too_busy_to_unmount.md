---
title: "External HDs won't format and too busy to unmount"
date: 2011-05-20
forum: Hardware
---

### Post by RogerD on 2011-05-20
Help

Having problems with external hard drives. I may be wrong, but I suspect they originated with an upgrade to 10.04 last Christmas. Around that time I also started using Amazon's S3 storage system, and, as a consequence, I stopped using my WD 80G external drive, previously used to backup my important files. 

A week or so ago I decided to start using the WD drive again. I can't remember exactly what I did, but it wasn't happy - never caused any problems before. When I plug it in, the on-off light as the front keeps flashing on and off, and when I try to remove the drive I get the message:

Error unmounting volumne
An error occured while performing an operation on "My Book" (Partition 1 of WD 800BB External): The device is busy

Details: Cannot unmount because file system on device is busy

The file system on the WD HD is FAT32, and the file system on my internal HD is ext4. Thinking that my problem be due to some sort of incompatibility issue, I attempted to refortmat the WD HD as ext4. All went well at first, but after about 10 minutes, the format process stopped, and I got the message:

Error formatting volume
Error creating file system: helper exited with exit error code 1:
Error calling fsync(2) on /dev/sdb1: input/output error

Assuming that my WD HD had died - it's about 5 years old - I bought a 160G Samsung S-Series drive - my but they do look neat! Unfortunately, this doesn't seem to have solved my problem. I have exactly the same problems with the Samsung drive - I can't format it and I can't unmount it.


Any ideas, anybody?

Roger D

---

### Post by Grenage on 2011-05-20
Hi Roger,

Are the errors exactly the same for the new drive? Are you able to begin the format process at all?  Are all of these processes being done through the GUI?

Open a terminal and type:

```
sudo fdisk -l
```

What do you get back?  I'm going to assume that just about every pre-packaged external drive is already partitioned and formatted to FAT32.

---

### Post by RogerD on 2011-05-20
Hi Grenage

Many thanks for the response.

Yes, as far as I can tell, the responses are the same.

Yes, I can begin the format process on both HDs.

All these operations are being done through the GUI.

With the WD, My Book, drive plugged in, sudo fdisk -1 yields:


roger@roger-desktop-new:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad737

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150253568   83  Linux
/dev/sda2           18706       19458     6034433    5  Extended
/dev/sda5           18706       19458     6034432   82  Linux swap / Solaris

But this might all relate to my internal HD, I'm not sure, not exactly a terminal expert.

Roger D

---

### Post by Grenage on 2011-05-20
You are indeed correct, sda1 will be your internal drive; does anything show up with the Samsung drive?

It's also worth running:

```
lsusb
```

When the devices are plugged in, it will hopefully at least list them there.

---

### Post by RogerD on 2011-05-20
Here's the output of lsub:


roger@roger-desktop-new:~$ lsusb
Bus 008 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:009d Microsoft Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04e8:1f01 Samsung Electronics Co., Ltd 
Bus 002 Device 003: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03f0:7611 Hewlett-Packard 
Bus 001 Device 003: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
roger@roger-desktop-new:~$ 

Both drives are indeed list.

Roger D

---

### Post by Grenage on 2011-05-20
Do these external drives have external power supplies, or are they drawing their power from the USB port? It's not uncommon for the computer to not dish out enough juice for the drive to operate properly.  If they come with optional power supplies, it might be worth trying them.

---

### Post by DeElent on 2011-05-20
I find that I have the same problem with a USB flash drive. for example, I attempted to reformat the USB drive i used to install 11.04 on a friends computer (as it is my only flash drive) and I received the same error messages as posted by Roger. I ended up using a Micro$haft machine to reformat it.

---

### Post by RogerD on 2011-05-20
I don't think it's a power supply problem. The WD HD has always had an external power supply

---

### Post by RogerD on 2011-05-20
Interesting suggestion. I've got windows XP installed, running under Virtual Box, I'll give it a try.

---

### Post by Grenage on 2011-05-20
I'm just running through possible causes; if there's an external power supply then it's a moot point.

If you boot from a liveCD (assuming you have one), are the drives detected?  This will at least rule out install-specific problems.

---

### Post by RogerD on 2011-05-20
Alas, didn't work, XP didn't detect any of my drives

---

### Post by RogerD on 2011-05-20
I've got a live CD - I'll give it a go.

---

### Post by RogerD on 2011-05-20
OK, I've booted from the live CD, mounted both external HDs, and tried formatting the WD device, with FAT32 this times. The result is exactly the same - the formatting seems to be going along fine, but then I get a formatting error message.

---

### Post by Grenage on 2011-05-20
So they at least show up when booting from a CD?  In that case, could you try partitioning and formatting them from a command line?

```
sudo fdisk /dev/xxx
```

Where xxx would be the drive, such as sdb, sdc (not sdb1, sdc1).  From there you should be able to print out, delete and create new partitions.

Once done, try formatting it using:

```
sudo mkfs.ext3 /dev/xxxx
```

Where xxxx is the partition, such as sdb1, sdc1 (not sdb, sdc).

---

### Post by RogerD on 2011-05-20
Ah, now you've lost me.

Using the Disk Utility, I've found the WD HD as /dev/sdb1. So  the command is sudo fdisk /dev/sdb right? Seems a bit hairy, an a instead of a  b and I could be messing with my internal HD

What do you mean by 'print out, delete and create new partitions?

---

### Post by PowerBarry43 on 2011-05-20
You could try using a Gparted liveCD which you can download here: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

hope that helps

Barry

---

### Post by RogerD on 2011-05-20
Hi Barry

Thanks for joining in. I've already tried Gparted, but the format option is greyed out

---

### Post by Grenage on 2011-05-20
> **RogerD said:**
> Ah, now you've lost me.

Using the Disk Utility, I've found the WD HD as /dev/sdb1. So  the command is sudo fdisk /dev/sdb right? Seems a bit hairy, an a instead of a  b and I could be messing with my internal HD

What do you mean by 'print out, delete and create new partitions?

Yes, you need to be very careful when using it.  If using the live CD, you could even unplug your computer hard drive.  If the option in Gparted is greyed out, then I would imagine that the drive has either not been partitioned, or is currently mounted.

---

### Post by RogerD on 2011-05-20
Happy to be careful, but I need to know where I'm going. Please confirm that
sudo fdisk /dev/sdb

is the correct command, and explain what you mean by  

print out, delete and create new partitions

---

### Post by Grenage on 2011-05-20
Well when you type:

```
sudo fdisk -l
```

It should list your current drives, and any partitions that are present; here is an example of the output on my computer:

```
Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4bea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf517ebd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
```

sda is my primary drive, and it holds three partitions which are labelled sda1, sda2 and sda5.  sdb is a generic data drive with one partition, labelled sdb1. Sorry if this is obvious, but it never hurts to be complete.

Let's assume that sdb is an external drive and we want to format it, first we'd run fdisk and reference that drive:

```
sudo fdisk /dev/sdb
```

You can press *m* for a list of commands; the most common being:

*p* Print/display the drive's current partitions.
*d* Delete a partition.
*n* Create a new partition (follow the prompts).
*t* Choose the ID type of a partition (83=Linux).
*w* Write changes and exit.

You would generally use them in that order, skipping the deletion or addition as is required.  Once that is done, you can format the partition using:

```
sudo mkfs.ext4 /dev/sdb1
```

All of this 'should' be possible through gparted.

---

### Post by RogerD on 2011-05-20
OK doing this, I've added a new partition, and I'm now being asked whether to input e extended or p primary partition (1-4)

Not quite sure what I'm doing, but what should it be?

---

### Post by Grenage on 2011-05-20
I'd go with Primary, since you're only using one partition (you're limited to 4 primaries per drive).

After that, the defaults should be fine; those are in brackets at the end of the question.

---

### Post by RogerD on 2011-05-20
Here's the result:

p
Partition number (1-4): 1
First sector (2048-156301487, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-156301487, default 156301487): 
Using default value 156301487

Command (m for help): 
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)

Looks as though I've still got a busy drive.

Makes you want to tear your hair out, but thanks for all your detailed help.

---

### Post by RogerD on 2011-05-20
Here's the result:

p
Partition number (1-4): 1
First sector (2048-156301487, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-156301487, default 156301487): 
Using default value 156301487

Command (m for help): 
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)

Looks as though I've still got a busy drive.

Makes you want to tear your hair out, but thanks for all your detailed help.

---

### Post by Grenage on 2011-05-20
Save your hair! ;)  It's possible that after a reboot the partition table *will* be used, so try that first.  If not, does this result in anything?:

```
sudo lsof /dev/sdx
```

Hopefully it will output anything that's locking the drive; I've never had to go this far.

---

### Post by RogerD on 2011-05-20
Reboot didn't help 

Not sure what to make of:


roger@roger-desktop-new:~$ sudo lsof /dev/sdx
[sudo] password for roger: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
lsof: status error on /dev/sdx: No such file or directory
lsof 4.81
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhlnNoOPRtUvVX] [+|-c c] [+|-d s] [+D D] [+|-f[gG]]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]] [-p s]
[+|-r [t]] [-s [p:s]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.
roger@roger-desktop-new:~$

---

### Post by Grenage on 2011-05-20
I'm an idiot; what I should have also added was that you need to replace *x* with whatever your drive number is.  For example:

```
sudo lsof /dev/sdb
```

---

### Post by RogerD on 2011-05-20
Hmm... interesting:

roger@roger-desktop-new:~$ sudo lsof /dev/sdb
[sudo] password for roger: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
roger@roger-desktop-new:~$

---

### Post by Grenage on 2011-05-20
Clutching at straws stuff, but after attempting to make the partition changes, does running this make any difference?

```
sudo partprobe /dev/sdb
```

Also, before trying to make the changes, ensure it's not being automounted (or trying to be):

```
sudo umount /dev/sdb1
```

---

### Post by RogerD on 2011-05-20
Hmm.... again


roger@roger-desktop-new:~$ sudo umount /dev/sdb1
roger@roger-desktop-new:~$ 
roger@roger-desktop-new:~$ sudo partprobe /dev/sdb
roger@roger-desktop-new:~$ 

Disk Utility tells me the drive is unmounted

---

### Post by Grenage on 2011-05-20
> **RogerD said:**
> Hmm.... again


roger@roger-desktop-new:~$ sudo umount /dev/sdb1
roger@roger-desktop-new:~$ 
roger@roger-desktop-new:~$ sudo partprobe /dev/sdb
roger@roger-desktop-new:~$ 

Disk Utility tells me the drive is unmounted

I'm running out of things to suggest, although I'm happy to have a peruse on google.  Does anything relevant appear in /var/log/syslog?

---

### Post by RogerD on 2011-05-20
Thanks for all your help - I've got to shut the PC down now, going out for the evening.

I'm thinking of taking the drives round to a friend, with a Windows PC, and reformatting to FAT32 under Windows.

If inspiration strikes do let me know

---

### Post by RogerD on 2011-05-21
SOLVED

Oh dear.. finally got to the bottom of this one.

Both my external HDs were connected to USB port on an expansion card - fitted at the same time as I upgraded to 10.04. When I connected the Samsung drive to a spare USB port on the front of my PC, everything worked perfectly.

Anyway, thanks for everyone's help - I'll have to put this down to experience. There's nothing wrong with 10.04.

Roger D

---

### Post by Grenage on 2011-05-22
Glad to hear it! I didn't bother suggesting another port, as you had two devices.  The expansion card is at least an easy fix. :)

---

