---
title: "External Hard Drive"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by Nickoladze on 2005-12-26
so i got a USB 2.0 external hard drive and i plug it in and linux detects it, shows up in computer and on desktop but i cant write to it... it shows up in /media/usbdisk/ too

im not sure what to so here

and btw, im a new linux user too, so the answer might be something simple but i dont know it

---

### Post by aysiu on 2005-12-26
See the fourth link in my sig.
I know it's not a partition, but the same rules apply.

---

### Post by Nickoladze on 2005-12-27
hmm i tried to follow it but i dont think it worked, but when i ran sudo fdisk -l i got:
> Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3495    28073556   83  Linux
/dev/hda2            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris
[B]
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes[/B]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

that bolded part is the hard drive i want to add, so does that mean its mounted properly? cause when i select it, it says the disk is read-only... hmm

---

### Post by towsonu2003 on 2005-12-28
[QUOTE=Nickoladze]/dev/sda1 1 30401 244196001 7 HPFS/**NTFS**
when i select it, it says the disk is read-only... hmm[/QUOTE]
oh thats bc it's ntfs... there is no write support for ntfs filesystems in linux... (okay, there is, but it is experiemntal and dangerous)

you could format it as FAT32 and use it read+write both in windows and linux though...

Offtopic note: it is weird that they formatted that external drive as NTFS...

---

### Post by Nickoladze on 2005-12-29
[QUOTE=towsonu2003]you could format it as FAT32 and use it read+write both in windows and linux though...[/QUOTE]


how would i go about doing that?

and are there any disadvantages to switching filesystems?

---

### Post by towsonu2003 on 2005-12-29
[QUOTE=Nickoladze]and are there any disadvantages to switching filesystems?[/QUOTE]
1. It will wipe all data in that hard disk (so do a **backup** before hand if there is any data in there)
2. It will require some reading on 
            a. how to use fdisk (command line) or qtparted (more friendly gui, in repos)
            b. partitions
3. The hard drive will become fragmented quicker

If you want to use it as a storage device, 3 doesn't count...

[QUOTE=Nickoladze]how would i go about doing that?[/QUOTE]

Hmm, you won't like this but, start reading this link and give it a try. Be careful not to wipe out your own primary harddisk (meaning, your device name to partition is **in this case** is /dev/sda)... 

Link is: [http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/)

good luck...

---

### Post by Krash1201 on 2005-12-29
i recomend qtparted, i usually use it after booting knoppix 3.9 which has it already.  it has some nice features.  i use it mostly to format fat32 partitions for my windows machines, and use the partitions for storage.  my external drive is 300 gig in fat32.  doesn't fragment much when just used for storage, but it doesn't hurt to keep tabs on it.  other benefit of fat32 partitions is just about any os can read it and linux can write to it.  this brings me to my problem that is close to this issue.

i am using a shuttle xpc sk41g as my base system with a 40 gig drive containing win2k on a five gig partition, fresh kubuntu install on a 10 gig partition, and a 25 gig fat32 partition.  unfortunatley, this is all fdisk -l returned when my 300 gig usb drive was plugged into the computer.  automount didn't recognize it either.  the drive is a 300 gig maxtor sata drive.  the goal is to use it for network storage and stream media from the 300 gig drive.  any ideas on a solution?  thanks in advance.

---

### Post by Nickoladze on 2005-12-30
i formattedit with QTParted to FAT32, but when mounting i get this:
> mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount


fdisk -l shows:
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    b  W95 FAT32


edit: it seems qtparted says its an unknown format type even when i reformat over and over to fat32, so i guess im using ext3 instead...

---

### Post by towsonu2003 on 2005-12-30
here are some things to do:

1. unplug the device, wait for a minute, plug it and do ```
dmesg | tail
``` to see why it is not automounting... the output should give you a clue. (post it here if necessary)

2. if there is no clue there, what command did you use to mount it? 
check with ```
mount
``` to see if it's already mounted (output will mention /dev/sda1 if it is)

3. if not listed above as mounted, try the following ```
sudo mkdir /media/usbfat32
sudo mount -t vfat /dev/sda1 /media/usbfat32
``` and to unmount (when you are done), use ```
sudo umount /media/usbfat32
``` (although ubuntu is supposed to automount it. )

---

### Post by Krash1201 on 2005-12-30
nick,

as far as i know, when you set the filesystem type to make the "partition" mount, fat32 should be vfat, i would try making that change before swicthing entirely to ext3.  qtparted could also have messed up, i have never used it in ubuntu, i usually use knoppix, and i don't usually have problems.

tosanu,

i tried what you suggested, but this is what i recieved:

```
user@theansweris42:~$ dmesg | tail
[4294716.540000] Bluetooth: L2CAP ver 2.7
[4294716.540000] Bluetooth: L2CAP socket layer initialized
[4294716.569000] Bluetooth: RFCOMM ver 1.5
[4294716.569000] Bluetooth: RFCOMM socket layer initialized
[4294716.569000] Bluetooth: RFCOMM TTY layer initialized
[4294718.637000] NET: Registered protocol family 10
[4294718.638000] Disabled Privacy Extensions on device c02eb280(lo)
[4294718.638000] IPv6 over IPv4 tunneling driver
[4294879.986000] NET: Registered protocol family 17
[4294890.301000] wlan0: no IPv6 routers present
user@theansweris42:~$ sudo mkdir /media/usbfat32
Password:
user@theansweris42:~$ sudo mount -t vfat /dev/sda1 /media/usbfat32
mount: special device /dev/sda1 does not exist

```

could my motherboard be the problem?  when i install windows on this machine, i always have a problem getting the usb drivers to install if i haven't registered windows.  could the same problem be preventing the hotplug subsystem from working properly?

---

### Post by towsonu2003 on 2005-12-30
> **Krash1201]
tosanu (*that's me?  said:**
>  Bluetooth: L2CAP ver 2.7
[4294716.540000] Bluetooth: L2CAP socket layer initialized
[4294716.569000] Bluetooth: RFCOMM ver 1.5
[4294716.569000] Bluetooth: RFCOMM socket layer initialized
[4294716.569000] Bluetooth: RFCOMM TTY layer initialized
[4294718.637000] NET: Registered protocol family 10
[4294718.638000] Disabled Privacy Extensions on device c02eb280(lo)
[4294718.638000] IPv6 over IPv4 tunneling driver
[4294879.986000] NET: Registered protocol family 17
[4294890.301000] wlan0: no IPv6 routers present
user@theansweris42:~$ sudo mkdir /media/usbfat32
Password:
user@theansweris42:~$ sudo mount -t vfat /dev/sda1 /media/usbfat32
mount: special device /dev/sda1 does not exist

```
could my motherboard be the problem?  when i install windows on this machine, i always have a problem getting the usb drivers to install if i haven't registered windows.  could the same problem be preventing the hotplug subsystem from working properly?
krash1201:
In your case, I see that after plugging in the external drive, dmesg does not report anything at all. dmesg is supposed to report something when you plug in stuff... what does sudo fdisk -l gives you after plugging in this drive (i.e. post in here :) )? in addition, try the same thing (unplug, wait some time, plug in, wait some time, dmesg | tail) but wait a little bit more this time (just in case). if dmesg reports nothing at all about the external drive, I would also open up a new thread specifically for this...if that is the case (no dmesg output after plugging in device), I'd say your problem is different (definitely out of my league). if you open up a new thread, post in the output of sudo fdisk -l ; cat /etc/fstab ; and dmesg | tail (after plugging) ; as well as the details of this thing/drive. 

Nickoladze: I'll be waiting for a failure/success post ;) I agree with krash1201's suggestion to try a little bit more bf switching it o ext3 bc. external storage is always nicer when you can plug it to any OS (hence fat32)-

---

### Post by Nickoladze on 2005-12-30
my friend knows some linux and told me to do something like what you said
```
sudo mount -t vfat /dev/sda1 /usbdrive/
```

and that wouldnt do it, i also tried just clicking the icon in computer, thats what gave the error i posted

and krash, in QTParted it makes you choose the format type from a dropdown list, FAT32 is what a chose, theres no vfat.

so i did format to ext3 and it works fine, i dont really plan on connecting it to a windows machine

---

### Post by towsonu2003 on 2005-12-30
[QUOTE=Nickoladze]
so i did format to ext3 and it works fine, i dont really plan on connecting it to a windows machine[/QUOTE]
if you ever need, this link may be beneficiary: [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
Though not sure how well it would work in removable devices, I used to use it (until recently) to copy my files on ext3 to Windows...

as for vfat, I'm not familiar with terms so I will say: you format it as fat32 and tell fstab/mount that its filesystem is vfat (instead of fat32, which isn't an option to mount) :)

---

### Post by CarlFK on 2006-01-05
> oh thats bc it's ntfs... there is no write support for ntfs filesystems in linux... (okay, there is, but it is experiemntal and dangerous)

[http://en.wikipedia.org/wiki/Captive_NTFS](http://en.wikipedia.org/wiki/Captive_NTFS)  (never used it, but it may be worth mentioning)

> you could format it as FAT32 and use it read+write both in windows and linux though...

Better yet, format it EXT3 and use [http://www.fs-driver.org](http://www.fs-driver.org) to mount it under windows.  This one I use quit a bit - no problems.

---

### Post by Nickoladze on 2006-01-06
ive been using it for awhile but im moving some songs over to it now (drag and drop in nautilus) and it wouldnt load so i did this in terminal:
> aj@AJComputer:/$ sudo cp /home/aj/Music/Rob\ Zombie/Past,\ Present,\ And\ Future/05\ -\ Super\ Charger\ Heaven.mp3 /media/usbdisk/Music/Rob\ Zombie/Past,\ Present,\ And\ Future/05\ -\ Super\ Charger\ Heaven.mp3

and got this error:

> cp: reading `/home/aj/Music/Rob Zombie/Past, Present, And Future/05 - Super Charger Heaven.mp3': Input/output error

is the file corrupt?

---

### Post by towsonu2003 on 2006-01-07
found this, but not sure if it will help: [http://lists.gnu.org/archive/html/bug-coreutils/2005-07/msg00211.html](http://lists.gnu.org/archive/html/bug-coreutils/2005-07/msg00211.html) but you could post the output (see command from its reply) for other forum readers (over my head)...

does that particular file open in a mp3 player (like totem, from gnome-terminal)? there may be some type of corruption in that file.

---

### Post by Nickoladze on 2006-01-07
yeah after i posted i tried playing the file, its corrupt

---

### Post by Ubuntuud on 2006-01-17
How do you format to FAT32?

---

### Post by athem on 2006-01-24
For what it's worth, here's how it did it.

(1) I purchased a Maxstor 200 GB external USB hard drive that I wanted to use for backup of my desktop and laptop Ubuntu systems.  The drive was originally formatted for NTFS, which can only be mounted read-only.  I really didn't want or need to reformat to FAT32, since I planned to only use it with Linux.

(2) When the drive was connected to my laptop (running Breezy), it showed up as a USB Drive on my desktop, but as mentioned above, was read-only.

(3) I installed qtparted, a GUI disk partitioning program (probably available in Synaptics, depending on where you have your repositories/ apt-source(s) set to).

(4) Unmounted the drive using umount /dev/sdb1 (drive name will vary depending on your system).

(5) Used qtparted to delete the old NTFS partition, repartition to ext3, made the partition active, and chose "Commit."

Note: I then tried to format the disk within qtparted, but the program failed...so

(6) I rand the Disks utility from the System panel menu, chose the drive, and formatted it.

(7) Created a mount point for the disk in my local directory.  Mounted it using mount -t ext3 /dev/sdb1 /home/athem/usbdrive

(8) Changed the ownership of the mount point to me, using from a root terminal (or sudo from any terminal):

chown athem /home/athem/usbdrive
chgrp athem /home/athem/usbdrive

I later added the drive to my fstab (/etc/fstab) as follows (using vi) because I plan to use it every time I start up:

/dev/sdb1 /home/athem/usbdrive ext3 defaults

Works fine.  I often use gFTP to connect to any of my local machine and transfer files.  Really should set up NFS to access all drives on my network...

Hope that helps.  Thanks to everyone above who basically figured all this out!

---

