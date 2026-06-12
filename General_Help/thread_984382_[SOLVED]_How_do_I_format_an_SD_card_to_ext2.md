---
title: "[SOLVED] How do I format an SD card to ext2?"
date: 2008-11-16
forum: General Help
---

### Post by fogelfink on 2008-11-16
I am not sure what I am missing, but I seem unable to format SD cards on my Ubuntustudio 8.10 machine!

The SD card shows up in nautilus, I can mount and unmount it, but I can't see it in the partition editor (gparted) :confused:, so how do I get the SD card to be recognized? 
Since I would like to use the SD card as a memory expansion on my AspireOne I would need to format it to ext2.
Thanks for your help.

[COLOR="Red"]For those experiencing similar problems the solution using the partition editor gparted is as follows:
Find out name/location of your SD card with:
[/COLOR]```
sudo mount
```
[COLOR="Red"]Then open gparted using the terminal[/COLOR]
```
gksudo gparted /xxx/xxx (the path to your card)
```
:) thanks to psusi for solving this one for me!

---

### Post by Mardoct909 on 2008-11-16
Was it mounted (Probably showing a desktop icon for it) at the time? It will show up in nautilus, mounted or no, so ensure it is mounted.

---

### Post by boof1988 on 2008-11-16
Does it show up on the output of the following Terminal command?:

```
sudo fdisk -l
```

Here's a representative example of my system with only the internal drive (without an external drive):

```
ubuntutest@bs-laptop:~$ sudo fdisk -l
[sudo] password for ubuntutest: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fd19fd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        8985    51199155    7  HPFS/NTFS
/dev/sda3            8986       12161    25511220    5  Extended
/dev/sda5            8986        9240     2048256   82  Linux swap / Solaris
/dev/sda6            9241       10700    11727418+  83  Linux
/dev/sda7           10701       12161    11735451   83  Linux
ubuntutest@bs-laptop:~$
```

[COLOR="Blue"]In my system, drives wont show up on /home/user/Desktop when they are not mounted.  But they will show up on the Nautilus menu (I assume it is so you can mount the drive from Nautilus).[/COLOR]

---

### Post by oilchangeguy on 2008-11-16
> **fogelfink said:**
> I am not sure what I am missing, but I seem unable to format SD cards on my Ubuntustudio 8.10 machine!

The SD card shows up in nautilus, I can mount and unmount it, but I can't see it in the partition editor (gparted) :confused:, so how do I get the SD card to be recognized? 
Since I would like to use the SD card as a memory expansion on my AspireOne I would need to format it to ext2.
Thanks for your help.

if you right click on the desktop icon, is one of the options format?

---

### Post by fogelfink on 2008-11-17
Thanks for the replies.  As I wrote before, the SD card does show up in nautilus, I can read and write data on it, but I does not show up in gparted.
Trying the command 

> sudo fdisk -l
gives me the following:

 > Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30370   243946993+  8e  Linux LVM
/dev/sda2           30371       30401      249007+   5  Extended
/dev/sda5           30371       30401      248976   83  Linux

This seems to indicate that the SD card is not there, does it?
In fact every time I start the partition editor I get the following error message, which I do not know what it means and what I have done wrong.
> The kernel is unable to re-read the partitiontables on the following devices:
- /dev/mapper/ubuntustudio-root

Thanks again for your help.

---

### Post by fogelfink on 2008-11-17
Me again,  I have just tried the same on my AspireOne, which runs Ubuntu 8.10 with netbook remix, but the result is the same:

SD cards though read/writable don't show up in the partition editor!

---

### Post by starcannon on 2008-11-17
Very odd that you can view it using Nautilus and not Gparted, if anything it usually works the other way around; that said, and while I know this is about to sound like beating a dead horse, perhaps running the gparted liveCD may be of use.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Try booting from that CD with the MMC card in its slot, and see if you can get it to show up; I'm further baffled that nautilus will use the card while fdisk won't? Going to work on unraveling the chewbaca defense, thats all thats left.

---

### Post by fogelfink on 2008-11-17
Thanks starcannon, but unfortunately I get the same result from the live cd of gparted.
The SD card does not show up!
I have yet again tested that it works in nautilus - and I can read/write onto the card.
Indeed very strange, and as I said it is not just on one machine, but on both of my computers.  One is running Ubuntustudio 8.10 and the other Ubuntu 8.10.

---

### Post by starcannon on 2008-11-17
If you have access to a windows box, r-click format it to fat32 or fat16, bring it back to linux box and try again, least thats what I'd do... that or replace the lil fish fecies ;)

---

### Post by fogelfink on 2008-11-17
Since I don't have a windows machine, I tried the formatting on a Mac, but no the result is the same as before!

---

### Post by psusi on 2008-11-17
What do you mean you need it to be ext2 so you can "use it as memory expansion"?

If you want to format it, then find out which device it is by looking at sudo fdisk -l, then format it with sudo mkfs -j /dev/XXX.  The -j enables the journal essentially making it ext3, which is a good idea.

---

### Post by fogelfink on 2008-11-17
Never mind why I would like to format it as ext2 (in case you are interested here's the reason: [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)).

> **psusi said:**
>  find out which device it is by looking at sudo fdisk -l,

As I wrote earlier, fdisk does not detect the SD card, so I can't format it in any way.  The amazing thing is however, that nautilus can read and write to the card, despite fsdisk not recognising it.  I repeat myself here, this is not just on one Ubuntu 8.10 machine, but two AND the same happens with different SD cards!
Is this a bug? Has anyone else tried formatting SD cards in Intrepid?

---

### Post by psusi on 2008-11-17
Maybe I missed it, but the only thing I saw about an SD card in that guide was installing a bootable system on it.  When you said "use it as expanded memory" it sounded like you were wanting to put a swap file on it or something, which doesn't require ext[23] at all.

While you have the thing mounted in nautilus, take a look at the output of:

```
sudo mount
```

---

### Post by fogelfink on 2008-11-18
Hi psusi,
the output of sudo mount gives me the following for the SD card
> /dev/mmcblk0p1 on /media/UNTITLED type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

But I have no idea what that means in terms of formatting, thanks for your time.

---

### Post by psusi on 2008-11-18
Then the device in question that you want to mkfs is /dev/mmcblk0p1.

---

### Post by fogelfink on 2008-11-18
> **psusi said:**
> Then the device in question that you want to mkfs is /dev/mmcblk0p1.

Thanks that did the trick!

I would still have a question though:  How do I reformat it to another format, just in case?  Is there no GUI way to format my SD cards, or at least some command with a dialog in terminal?

---

### Post by psusi on 2008-11-18
Yea, gparted.

---

### Post by fogelfink on 2008-11-18
> **psusi said:**
> Yea, gparted.

???????????????

Did I forget to mention that gparted is the problem?

Though I was able to format the SD card with mkfs, still neither of my ubuntu machines will let me access the ext2 formatted card (or any other for that matter) via gparted.  The card does not show up in the device list!  How do I tell gparted the path to my SD card if it does not recognise it by itself?  Am I missing something obvious?

---

### Post by psusi on 2008-11-18
Pass the device name to gparted when you run it.

gksudo gparted /dev/mmcblk0p1

It probably doesn't show in the drop down list in the gui because it has a funky name.

---

### Post by Illuminated on 2009-02-08
I got the same problem as fogelfink but my mount looks like this : 

zi33@zi33-laptop:~$ sudo mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zi33/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zi33)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=zi33)
 
So what do i do in my case???

---

