---
title: "USB Hard drive corruption"
date: 2004-12-07
forum: Hardware &amp; Laptops
---

### Post by felixruina on 2004-12-07
Well, this is my first time posting, so go easy on me.

I've been running Ubuntu as my sole desktop OS for some time now.  The only issue I have not been able to resolve is with my FAT32 formatted 160GB Western Digital USB2.0 HD I use for portable storage.  The drive automounts just fine, it shows up on my desktop, I can view it in nautilus or bash without any difficulty at all--until I actually start using it for any length of time.  I've noticed the problem when I've made large file (>200MB) transfers from the USB drive to the internal drive, or vice versa.  It will begin the transfer, and then after working just fine, it will all of a sudden hang.  The same thing happens whether I use nautilus or bash.  If I cancel the process and go to browse the drive again, any file that has been accessed since the mount does not show up anymore.  (Thank God the files are still there--I can access them again by remounting the drive)  The strange thing is that the hang seems to be random.  Sometimes the drive will work with no difficulty for transfering or accessing several large files in a row, but it will inevitably eventually hang, and the only solution is remounting the drive, and even then, if the computer is not rebooted, the hang will occur almost immediately.

I will I had some sort of debug logging info to give, but I never get any errors, so I wouldn't no where to look.  I am just using the USB hub of my motherboard which is a soyo Via KT-400 board.  My other specs, in case they help:  AMD Athlon XP 2100+; 1GB DDR333 RAM; ATI Radeon 9600pro; SBLive5.1; 12GB and 40GB internal HDs, running Ubuntu with Hoary updates.

Hopefully someone might have some insight.  Thanks in advance for the help.

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=felixruina]Well, this is my first time posting, so go easy on me.[/QUOTE]

How about a welcome then.

[QUOTE=felixruina]I've been running Ubuntu as my sole desktop OS for some time now.  The only issue I have not been able to resolve is with my FAT32 formatted 160GB Western Digital USB2.0 HD I use for portable storage.  The drive automounts just fine, it shows up on my desktop, I can view it in nautilus or bash without any difficulty at all--until I actually start using it for any length of time.  I've noticed the problem when I've made large file (>200MB) transfers from the USB drive to the internal drive, or vice versa.  It will begin the transfer, and then after working just fine, it will all of a sudden hang.  The same thing happens whether I use nautilus or bash.  If I cancel the process and go to browse the drive again, any file that has been accessed since the mount does not show up anymore.  (Thank God the files are still there--I can access them again by remounting the drive)  The strange thing is that the hang seems to be random.  Sometimes the drive will work with no difficulty for transfering or accessing several large files in a row, but it will inevitably eventually hang, and the only solution is remounting the drive, and even then, if the computer is not rebooted, the hang will occur almost immediately.

I will I had some sort of debug logging info to give, but I never get any errors, so I wouldn't no where to look.  I am just using the USB hub of my motherboard which is a soyo Via KT-400 board.  My other specs, in case they help:  AMD Athlon XP 2100+; 1GB DDR333 RAM; ATI Radeon 9600pro; SBLive5.1; 12GB and 40GB internal HDs, running Ubuntu with Hoary updates.

Hopefully someone might have some insight.  Thanks in advance for the help.[/QUOTE]

Wow, your system is really close to mine. As for advice, I have a big one and a small one.

First I have to ask a question: Did you ever try this in Warty? Because Hoary (In my own opinion) is very buggy right now. On my desktop, I don't care. If hoary kills it I reformant and file a bug report. But if this problem kept happening to me in Hoary that was a show stopper, I would stop testing. Try putting on warty an see if it helps. 

Other advice- Use this guide to see if you can get it to load at boot. It might work better that way.


[http://kitech.com.my/ubuntu/4.10/index.html#automountntfs](http://kitech.com.my/ubuntu/4.10/index.html#automountntfs)

---

### Post by felixruina on 2004-12-08
Thanks so much for your prompt reply!

I must admit that I have not tested it out on warty--I guess I'm just one of those guys that likes the latest and greatest, bugs and all, but I'll try to get warty installed this weekend and see what happens.  As far as mounting the drive at boot via fstab, I've found that that makes no difference as far as the problem is concerned.

Thanks again for your help.

---

### Post by jeremy on 2004-12-08
I have exactly the same problem, but am using Warty.

---

### Post by poofyhairguy on 2004-12-08
[QUOTE=jeremy]I have exactly the same problem, but am using Warty.[/QUOTE]

This sounds serious, try to file a bug report!

---

### Post by felixruina on 2004-12-09
jeremy,
what are the specs of your system?

---

### Post by davegod75 on 2004-12-13
can i ask what command you are using to mount your usb hard dive.  I have an LACIE usb hard drive and I can't get it to mount correctly

/dev/sda7 on / type reiserfs (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/sda8 on /home type reiserfs (rw)
/dev/sda6 on /swap type ext3 (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/sda5 on /mnt/windows type ntfs (rw,umask=000)

I have tried: sudo mount /proc/bus/usb /mnt/LACIE -t ntfs -o umask=ooo

but it tells me /proc/bus/usb is not a block device

so i tried: sudo mount /proc/bus/usb /mnt/LACIE -t usbfs -o umask=ooo

that mounts but when I look at the drive it has wierd folders and what not.

---

### Post by felixruina on 2004-12-13
davegod,

it looks like you have a scsi system.  Is that right?  That might make it a little bit more difficult because usb devices are usually show up as scsi drives (/dev/sdxx).  So, since I use IDE drives, for me the usb drive is just the first scsi device:
[I]
sudo mount /dev/sda1 /media/mountdir[/I]

An easy way to figure out the /dev entry for the device is to plug the drive in, allow hotplug to detect it, and then type:

*tail /var/log/messages*

There should be a listing there like:

*kernel: Attached scsi disk sda at scsi1, channel 0, id 0, lun 0*

In this example, the /dev listing is /dev/sda

It may be that you already know all this and this is no help at all, but that's what I use to mount the drive.  Hotplug will also do it automatically for me, as well.  Does it not automount it for you?

Hope this helps.

---

### Post by davegod75 on 2004-12-13
I don't have scsi but my hd is SATA so that might have something to do with it.  

here is what the log says.

Dec 13 22:27:39 localhost scsi.agent[9319]: disk at /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host5 /5:0:0:0
Dec 13 22:27:40 localhost kernel: VFS: Can't find a valid FAT filesystem on dev sdb1.
Dec 13 22:27:40 localhost kernel: UDF-fs: No VRS found
Dec 13 22:27:40 localhost kernel: Unable to identify CD-ROM format.
Dec 13 22:27:40 localhost kernel: HFS+-fs: unable to find HFS+ superblock
Dec 13 22:27:40 localhost kernel: VFS: Can't find a HFS filesystem on dev sdb1.
Dec 13 22:27:40 localhost kernel: VFS: Can't find ext2 filesystem on dev sdb1.
Dec 13 22:27:40 localhost kernel: ReiserFS: sdb1: warning: sh-2021: reiserfs_fill_super: can not find reise rfs on sdb1
Dec 13 22:27:40 localhost kernel: XFS: bad magic number
Dec 13 22:27:40 localhost kernel: XFS: SB validate failed


and no, it does not auto mount.  My usb drive is formatted NTFS 

I'm consider myself a newbie so i'm still stuck on what to do now.

---

### Post by felixruina on 2004-12-14
Okay, great.  It looks like your usb drive should be located at /dev/sdb.  Does it have multiple partitions?  If it is only 1 partition, then the address of the partition will be /dev/sdb1, and this is what you will mount.  To be sure this is the right drive, you can type in *fdisk -l*, and this will list all of the connected drives, mounted or not.  /dev/sdb should be there, and the filesystem should be listed as "ntfs."  The other issue is that you might not have NTFS support enabled.  Try this first of all:
[I]
sudo mount -t ntfs /dev/sdb1 /mountdir[/I]

the "-t" option lets you tell the mount command which file system you are mounting (in this case ntfs), and the /mountdir is where you want the file system mounted to.  Be sure and put this somewhere that doesn't require root priviledges (like /home/username/mountdir) otherwise you'll have to *sudo su* just to browse in it.

If ntfs support is not enabled, then it is a more difficult matter and the mount command will return with an error.

Let me know what happens.

-felix

---

### Post by davegod75 on 2004-12-15
Thanks..that worked..

---

### Post by rolfpal on 2004-12-15
I have a firewire disk that I use on my desktop (shuttle p4 2.4G) and sometimes on my laptop (Sony F650 P3 600) and I have found that it will not behave unless I tell sbp2 to serialize the io

do

**sudo nano /etc/modules**

then add a line that reads
[B]
sbp2 serialize_io=1[/B]

Cheers,

---

### Post by piedamaro on 2004-12-21
Same issue here: when I plug an ntfs usb disk, I have this in log/messages:

Dec 21 19:44:22 ubuntu kernel: usb 1-1: new full speed USB device using address 22
Dec 21 19:44:22 ubuntu kernel: scsi19 : SCSI emulation for USB Mass Storage devi ces
Dec 21 19:44:22 ubuntu kernel:   Vendor:           Model:                   Rev: 
Dec 21 19:44:22 ubuntu kernel:   Type:   Direct-Access                      ANSI  SCSI revision: 02
Dec 21 19:44:22 ubuntu kernel: SCSI device sda: 31263 512-byte hdwr sectors (16 MB)
Dec 21 19:44:22 ubuntu kernel: sda: Write Protect is off
Dec 21 19:44:22 ubuntu kernel:  /dev/scsi/host19/bus0/target0/lun0: p1
Dec 21 19:44:22 ubuntu kernel: Attached scsi removable disk sda at scsi19, chann el 0, id 0, lun 0
Dec 21 19:44:22 ubuntu scsi.agent[8546]: disk at /devices/pci0000:00/0000:00:03. 0/usb1/1-1/1-1:1.0/host19/19:0:0:0
Dec 21 19:44:22 ubuntu usb.agent[8530]:      usb-storage: already loaded
Dec 21 19:44:23 ubuntu kernel: VFS: Can't find a valid FAT filesystem on dev sda 1.
Dec 21 19:44:23 ubuntu kernel: UDF-fs: No partition found (1)
Dec 21 19:44:24 ubuntu kernel: Unable to identify CD-ROM format.
Dec 21 19:44:24 ubuntu kernel: HFS+-fs: unable to find HFS+ superblock
Dec 21 19:44:24 ubuntu kernel: VFS: Can't find a HFS filesystem on dev sda1.
Dec 21 19:44:24 ubuntu kernel: VFS: Can't find ext2 filesystem on dev sda1.
Dec 21 19:44:24 ubuntu kernel: ReiserFS: sda1: warning: sh-2021: reiserfs_fill_s uper: can not find reiserfs on sda1
Dec 21 19:44:24 ubuntu kernel: XFS: bad magic number
Dec 21 19:44:24 ubuntu kernel: XFS: SB validate failed

The question is: why the kernel is trying to use all possible filesystem but ntfs?
Mounting manually it's not an option cause when I plug other devices (for ex. a vfat mp3 player which is being recognized and auto-mounted perfectly), the device node changes from sda to sdb etc.

Too sad that this works even with ntfs in fedora.
Does anyone has any clue? Recompiling the kernel with builtin ntfs could help?

---

### Post by rolfpal on 2004-12-27
I don't know if this is the same,but i had a very similar problem with a firewire drive.  I solved it by forcing the spb2 module to serialize.  It slows the system down but it now works reliably.  It doesn't aotomount hoever.

Cheers,

---

### Post by felixruina on 2004-12-29
[QUOTE=rolfpal]I don't know if this is the same,but i had a very similar problem with a firewire drive.  I solved it by forcing the spb2 module to serialize.  It slows the system down but it now works reliably.  It doesn't aotomount hoever.

Cheers,[/QUOTE]
 Thanks.  Unfortunately I'm away from my computer for the holidays, but I'll give that a shot when I get home and report back.

Happy Holidays to everyone.

---

### Post by ivan on 2004-12-30
hi everyone,

i find this thread very usefull, but i still have a question. i'm using warty (actualy for a month). in case i can't see any "sdx" devices in my /dev folder, does it mean that i have to recompile the kernel with scsi, usb mass- (or usb-) storage support? or there's something else i miss ....

i need this to access my digital photo camera (HP).

thanks, and have a goot time in the ney year night! cheers!

---

