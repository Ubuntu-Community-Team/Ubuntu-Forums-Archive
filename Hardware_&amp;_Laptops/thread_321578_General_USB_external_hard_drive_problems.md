---
title: "General USB external hard drive problems"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by Bigglez on 2006-12-19
**[COLOR="DarkOrange"]If you vote, please leave a note with a little more info.[/COLOR]**
**How reliable are external USB drives on Gnu/Linux?**
I started with Fedora Core 1. I moved up to FC 3. My two external hard drives (hdds) came with me. Now I'm on Kubuntu 6.06 and they are still there, and I'm on the same box as I always was and the same USB problem haunts me.
So, what's the beef? The drives are just plain unreliable and it's not the drives themselves. It could be the USB 2.0 widget on my computer, or it could be something about how Linux deals with it.

Here are the symptoms:
[LIST=1]
[*]When only SDA1 is mounted things work fine for days and weeks at a time.
[*]When I then plugin SDB1 - I can mount it and browse the drive fine -- for a while.
[*]If I do any heavy-duty copying of files from SDA1 to SDB1, SDB1 will work for a while (maybe 30 mins) and then BOTH drives freeze.
[*]Konqueror and any other things that touched those mounts will also freeze.
[*]I **can** sudo umount them.
[*]I **cannot** remount them.
[*]I must restart the machine. Restart Linux? The horror!
[*]I cannot unmount SDB1 and then re-mount it again. It just does not want to show up after an unmount.
[/LIST]

I have asked about this on and off on lists and forums and no-one really cares about it. It seems to be a real phenomena, but I suspect that we (Linux users) just "live with it".
I have asked if there aren't any "magic" commands that can reset the USB system so that one can get the drives working again after they have frozen themselves, but there seems to be nothing out there. No amount of sudo rmmod usb_storage seems to cut the mustard.

So, I thought I'd post a lonely poll: Who thinks USB hdds are unreliable? 
[B][I]Unreliable = You can't plug 'em in and rely on them being there until you unplug them. You certainly cannot plug/unplug (repeat) them...
[/I][/B]

I might screwby-doo the poll up I have never used one before...

/d

---

### Post by xyz on 2006-12-19
I've never had the slightest problem.
Post your computer specs and the outputs of:

```
sudo fdisk -l

and 

cat /etc/fstab
```


[Understanding fstab by bodhi.zazen]("http://ubuntuforums.org/showthread.php?t=283131")
> ...and no-one really cares about it.
You must be one of the very first persons to say this here! Not really the type of thing/attitude people here like to hear...so many mods and others busts their .....on a daily basis. It is simply untrue!
Good luck anyways and let us know how it goes.

**EDIT: I clicked NO by mistake.**

---

### Post by Bigglez on 2006-12-19
xyz,
I am not moaning or wailing and I am not disparaging the mods or the coders - I am just stating a fact as I see it from my perspective. I restarted my machine (again) today, so that got me a little steamed! But only with the hardware. It's not a "fix this or I'll go back to Win... waaaah!" situation. :)

I hope you can give me a clue about this, it's not been something anyone else has been able to nail. In the end it could just be my hardware.

```

~:$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hda3 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/hdb1 /media/music ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/hda2 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

#/dev/sdb1 /media/maxtor300 ext3 user,noauto,atime,rw,nodev,noexec,nosuid 0 0
#/dev/sda1 /media/sda1 ext3 user,noauto,atime,rw,nodev,noexec,nosuid 0 0

```
You can see I remarked them out - I had tried to include them in the fstab, to see if that would help at all. But all it did was confuse the automount(?) or hotplug(?) stuff.


```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241   83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   83  Linux

```

And - I figured you clicked the wrong poll option! :D

---

### Post by Bigglez on 2006-12-20
Bump! Darnit!

---

### Post by Bigglez on 2006-12-24
Another bump!

---

### Post by xyz on 2006-12-25
nothing yet!

---

### Post by Bigglez on 2006-12-25
Me neither..

Happy End-of-year Thing !

---

### Post by xyz on 2006-12-25
OK Let me post my fdisk / fstab and see if it rings a bell to you as to which way to go from here.
> root@luser:~# fdisk -lu

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    30716279    15358108+   7  HPFS/NTFS
/dev/hda2        30716280    51199154    10241437+  83  Linux
/dev/hda3        51199155   153388619    51094732+   c  W95 FAT32 (LBA)
/dev/hda4       153388620   156296384     1453882+   f  W95 Ext'd (LBA)
/dev/hda5       153388683   156296384     1453851   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80060423680 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368015 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    30716279    15358108+   b  W95 FAT32
/dev/sda2        30716280   102398309    35841015    b  W95 FAT32
/dev/sda3       102398310   156360644    26981167+   b  W95 FAT32

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs-3g defaults,locale=en_US.utf8   0    0 


/dev/hda3       /media/hda3  vfat iocharset=utf8,umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
Check out how/where it's mounted. Note that my external drive sda1/2/3 are FAT 32 partitions.

---

### Post by Bigglez on 2006-12-25
I see there is no mention of sda in your fstab, so all-in-all it looks much the same as mine.

I see there are now 5 no's in the poll. So far it seems my experience with USB drives is the norm. Of course, 6 votes is a joke!

Let's see, I'll bump this a few times over the holiday period and then again a few days into January.

---

### Post by xyz on 2006-12-25
> I see there is no mention of sda in your fstab, so all-in-all it looks much the same as mine.
It does show in fstab! Don't look for it there.
It's in ''fdisk", an external HD partitioned in 3:
> Device Boot Start End Blocks Id System
/dev/sda1 63 30716279 15358108+ b W95 FAT32
/dev/sda2 30716280 102398309 35841015 b W95 FAT32
/dev/sda3 102398310 156360644 26981167+ b W95 FAT32 
in FAT 32.
Well 5 isn't much! Unless it's YOU who voted from 4 different IP's?? LOL!!!
BTW instead of voting only, they could post their experience. Could help others and themselves!

---

### Post by Bigglez on 2006-12-26
xyz, thanks for at least trying to help :)

Voting: I woudn't even know how to vote more than once!

I wish the other voters would post here, I can't understand why they don't - I wonder if it's something I did wrong in the poll?

---

### Post by xyz on 2006-12-27
> **Bigglez said:**
> xyz, thanks for at least trying to help :)

Voting: I woudn't even know how to vote more than once!

I wish the other voters would post here, I can't understand why they don't - I wonder if it's something I did wrong in the poll?
In general people here don't respond because:
1. nobody has an answer
2. they didn't like something in your post
I know, you explained...but people are very helpful here and they don't like to hear certain things. That MAY explain it.

I did a little "HD reliability linux" search and there's quite a bit on the subject.
What's the brand?

---

### Post by Bigglez on 2006-12-27
sda = Seagate 120 Gig
sdb = Maxtor 300 Gig

I have used the Maxtor under Windows for many hours without fail, so am fairly sure it works fine. The Seagate is always plugged into my Linux box (it's for backups), and it always works fine. When I plug the Maxtor in too, well ... ref. OP.

I'll try your google search too.

---

### Post by Bigglez on 2006-12-28
28 Dec - Bump!

---

### Post by xyz on 2006-12-29
[FAQ]("http://www.its.monash.edu.au/staff/systems/linux/technical/usb/usbhome-fc1.html")

---

### Post by Bigglez on 2006-12-31
thx 4 the link.

Last day of 2006 Bump!!!

Hope 2007 is good to Ubuntu and Co.

---

### Post by MoreLinux on 2006-12-31
I have 3 USB hard drives and use them all the time for everything. Never have any problems with them except for one the time I forgot to unmount them. ](*,)  Could recover with fsck without any problems. Now I always use the "Safely remove" option as I do in Windows XP.

---

### Post by Bigglez on 2006-12-31
Wish I was you :)

---

### Post by nik on 2006-12-31
My two works fine, a lot better than in windows. They actually both have some mechanical error, one from being in a lightning accident and the other just from long term use (taken from an old computer). In windows they keep having problems reading and writing, but in ubuntu there's no problem. except if I leave them plugged in when booting, than it hangs a few seconds when loading grub.

Oh, and I never unmount them before disconnecting... ;)

---

### Post by haimroman on 2006-12-31
Summary:
[LIST=1]
[*]My Ubuntu recognizes my USB stick but doesn't mount it automatically
[*]I keep getting HAL daemon errors.  Is this connected?
[/LIST]

I'm a UNIX sysadmin, but new to Ubuntu (& Debian).  I would have expected to be able to plug my USB stick (we call it disk-on-key in Israel), and have it automatically mounted.  

Ubuntu 6.10, Gnome

USB Hardware:
[LIST=1]
[*]Dynamode USB hub, 4-port, supports USB version 2, model: USB-H40-Micro-2.0
[*]USB Stick: Kingston USB 2.0 Data Traveler, 1 GB.  
[/LIST]

The stick is connected to the hub, of course.  The system does recognize the stick when it's plugged in.  /var/log/messages displays:

```

kernel:  usb 3-1.2: new high speed USB device using ehci_hcd and address 5
kernel:  usb 3-1.2: configuration #1 chosen from 1 choice
kernel:  scsi2 : SCSI emulation for USB Mass Storage devices
kernel:    Vendor: Kingston  Model: DataTraveler 2.0  Rev: PMAP
kernel:    Type:   Direct-Access    ANSI SCSI revision: 00
kernel:  SCSI device sda: 2015232 512-byte hdwr sectors (1032 MB)
kernel:  sda: Write Protect is off
kernel:  SCSI device sda: 2015232 512-byte hdwr sectors (1032 MB)
kernel:  sda: Write Protect is off
kernel:   sda: sda1
kernel:  sd 2:0:0:0: Attached scsi removable disk sda
kernel:  sd 2:0:0:0: Attached scsi generic sg0 type 0

```

And "sudo fdisk -l" shows:

```

...
Disk /dev/sda: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         126     1007584+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)

```

However, there is no automatic mount, as I would have expected.  
Now, I don't see any line in my /etc/fstab for /dev/sd* devices.  So, apparently, that's the problem.  I remember that my USB stick vendor has instructions on the web.

But I would have expected that Ubuntu would have included everything needed for having it mounted automatically.  When I connected the above HW to a CentOS 4 computer, the disk *was* mounted auomatically.  

**HAL daemon** - often when logging in, I get a message about not being to start the HAL daemon.  Someone suggested that it might be due to startup/config files in my home directory from an older version of Gnome.  Removing the files solved the problem, but it reappeared.  Migh this be connected?

Thanks

---

### Post by Bigglez on 2007-01-08
I really don't know about usb sticks. I suppose they are the same as external drives, but this thread is specifically a poll about USB hard disk drives, so you might be better served starting a new thread...

FWIW - I am sure you will get a lot of help by trying a search first, I have seen a lot of USB stick threads.

---

### Post by Bigglez on 2007-01-14
Bump and update. If I plugin a second USB HDD and then use it for only a few minutes then all is okay. It's when I leave it on and mounted for a while (maybe over 1 hour) that it will crash the **entire** usb storage system and my /dev/sda1 will crash as will all konqueror windows holding it.

C'mon over and vote and drop a message.
/s

---

### Post by Bigglez on 2007-01-26
*Almost end of Jan bump.*

10 (1 mistaken vote) peeps agree - external USB is not reliable when you have more than 1 drive.
4 say - no problemo.

Come and vote!
:D

---

### Post by allwin on 2007-01-26
I can't get my USB or 1394 HD enclosures to work worth a @#$%.  They only seem to work in USB 1.0 mode, at a blazing 1MB per second access time.  I did manage to get the one 1394 enclosure to work after I plugged in a DVD writer I have here, unplugged that, and plugged the enclosure in the same port.

I think there is a conspiracy of silence around here concerning external HD hardware.  You see the fanbois saying ohhh I've got dozens and never a problem but never any help or guidance.  It's like someone is trying to cover up the problems by ignoring them.

Same with audio, MIDI, and webcam problems.  If some enterprising folks got together and fixed this stuff instead of rewriting boring stuff like compilers every six months, they'd get a LOT more people won over to UBUNTU, IMNSHO.  It's crazy to have to keep windoze around just to play with the peripherals that don't work under Linux.  My main holdback.

---

### Post by Bigglez on 2007-01-27
The "conspiracy of silence" might be a bit strong, but you are right about there being no effective help for USB ware.

My USB hdd just crashed a moment ago. I only had ONE plugged in and it's been plugged-in and working for at least 24 hours.

Here is what my lsmod looks like and what it says when I try to remove the usbcore. I am **forced** to restart my computer before that drive will function again. What's going on here?

```

usbcore               130820  4 usb_storage,ehci_hcd,uhci_hcd
root@DDM:~# rmmod -f usbcore
ERROR: Removing 'usbcore': Resource temporarily unavailable

```

---

### Post by Bigglez on 2007-01-29
A bump while I can.

---

### Post by Al_maverick on 2007-01-30
I got problems with my USB drive too. After unplugging it, it froze konqueror. Now I cant even browse a regular folder with it. :(

---

### Post by freddyg on 2007-02-02
actually, i have some eratic problems with single or multiple devices, not so sure about what is causing them, still learning my way around logs and such. but i do notice problems with konqueror doing large transfers. it will typically crash out after 2-3 GB of info and i also have periodic problems recognizing a usb stick as well as the ext drives

---

### Post by Al_maverick on 2007-02-03
> **Al_maverick said:**
> I got problems with my USB drive too. After unplugging it, it froze konqueror. Now I cant even browse a regular folder with it. :(

I tracked down my problem to a misconfiguration in fstab. The usb drive was configured twice. That caused kded to lock up and take 99% of the CPU. I left only one line and now it seems to be working fine.

---

### Post by Bigglez on 2007-02-05
I am glad your issue was resolved, but I fear it may be an illusion. My drives are not in the fstab at all! They get recognized and put on the desktop automagically. (I have not worked out how)

The other frustrating thing is that if I plug in just one drive and switch it on --> sda1. Switch it off ... on --> sdb1. Of/On ---> sdc1
It creeps up one letter at a time, so I can never predict what sdX it will be on, so I can't put an fstab entry in for it.

AAAAgggghhhhh!

I am USB HDD blue
:(

---

### Post by justin whitaker on 2007-02-12
My drives are not in fstab as well. Like I posted in another thread, it's Ubuntu specific.

---

### Post by Calrefawena on 2007-02-16
I have a Freecom 400GiB disk, with three partitions (NTFS, ext3, and FAT32), and an iPod. Both work mostly fine, but until recently the NTFS partition refused to unmount in Konqueror (I'm using Kubuntu, if that matters), and I had to do it in the command line.

---

### Post by Bigglez on 2007-02-17
Not sure if a Freecom is external USB, will assume it is. Sounds like your troubles are different to the ones I experience. If you can unmount on the command line then I don't see a problem. You're good to go :)

---

