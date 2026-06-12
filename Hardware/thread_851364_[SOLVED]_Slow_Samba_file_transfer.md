---
title: "[SOLVED] Slow Samba file transfer"
date: 2008-07-06
forum: Hardware
---

### Post by AaronLS on 2008-07-06
Transferring files to my samba share is about 2.5 times slower than transferring them to a windows share. In both cases destination was to an entire hard drive shared.  No RAID on destinations.  The WinXP Pro machine had a 320 gb, and the linux has a 700gb.

This is my topology:
Linksys Cable Modem->Linksys Router(10/100)->Wired to:
WinXP pro SP2 machine 1
WinXp Pro SP2 machine 2
D-Link 10/100 switch->wired to:
Ubuntu Desktop
Ubuntu Server with Samba (was 7.10 upgraded to Hardy Herring/Haron or whatever).

The network cable between the Router and the D-Link switch is maybe about 15-20ft long.  All other cables are just a few feet long.  Switch indicates 100mbps connections.  I took the switch out and connected the long cable directly to the Samba share box, rebooted it, and did the transfer again with no improvement.

The Samba machine:
P3 650 mghz
900+ mb ram
OS on 18 gig hd(not sure how fast it is, probably original in the machine)
Share attached to a new Promise SATA300 TX4 pci controller card with the 700gb hard drive being the only drive connected to it.

I did not install the drivers for the SATA card because the CD only had windows drivers, and the linux drivers looked like they required making a floppy disk, and I don't have a floppy drive in this computer.  So I just installed linux hoping it would have the driver already.  The drive was mounted fine, so I assumed so.   Just wondering if the manufacturer driver would improve performance.  They only offer a SUSE and RedHat versions for linux.  Which should I try to use?

[http://www.promise.com/support/download/download2_eng.asp?productId=139&category=all&os=100&go=GO](http://www.promise.com/support/download/download2_eng.asp?productId=139&category=all&os=100&go=GO)

Thanks in advance.

---

### Post by AaronLS on 2008-07-06
Porion of my smb.conf, which I added the aio parameters to with no luck.

```


[global]
#asynchronous IO
aio read size = 1
aio write size = 1
aio write behind = true

...

[store]                
comment = Public Folder        
path = media/store
writable = yes     
force create mask = 777
force directory mask = 777
read only = no

```

---

### Post by AaronLS on 2008-07-06
I tried copying the test file within the linux system with something like:
cp some700mbFile some700mbFile2

Even though it is both reading and writing on the same drive, it took 2min 20 seconds, which is about the same time it takes to copy it from the windows machine to the linux machine.  Versus 1 minute copying from one windows machine to another.  So it seems to not be related to samba or the network.

Either my hardware is to blame, or some part of linux's use of the hardware.  Windows normally asks about something like block sizes when formatting a drive, which effects write performance for large files.  I don't remember a setting like this when I used gparted LiveCD to format my 700gb drive to NTFS.

---

### Post by AaronLS on 2008-07-06
It looks like I could make the drive some other file system instead of NTFS.  Could this potentially be a problem.  I see a lot of people in the past saying that linux can NOT write to a NTFS file system.  So perhaps this has been added in the alst couple years and perhaps isn't polished in terms of performance?

I will be copying files to and from the server quite a bit, some being several gigs and some being large groups of source code files(tons of very small files).

Am I correct in understanding that I can make the harddrive whatever filesystem I want and samba will still be able to serve it to other windows clients?
Any suggestions for a file system I should try?

---

### Post by AaronLS on 2008-07-06
Reformatted/partitioned (whatever the right term is) with GParted Live CD to ext3 file system instead of ntfs.  Changed fstab entry for the hard drive from ntfs to ext3.  Rebooted.

The copy from Windows to Linux is now only about 18% slower than the copy from Windows to Windows.  This is much better than the 150% slower it was before!

---

### Post by Sef on 2008-07-06
OP request to be moved to Hardware & Laptops.

---

