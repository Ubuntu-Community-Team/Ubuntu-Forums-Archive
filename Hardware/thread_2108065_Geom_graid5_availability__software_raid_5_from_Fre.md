---
title: "Geom graid5 availability / software raid 5 from FreeNas"
date: 2013-01-23
forum: Hardware
---

### Post by aaronjsmith21 on 2013-01-23
**_EDIT: To save people time before reading through all this and find nothing about Ubuntu and GEOM compatibility, this issue was not resolved, but my initial problem of recovering data from a FreeNAS Raid5 UFS File system has been and is discussed here. Thank you._**

Issue:
To see if geom graid5 is available on ubunutu as it is in FreeBSD to be able to access 3 of my drives from a FreeNAS system that I have. The software raid used UFS for the file system so I am sure the disks will be read only, but I need to be able to access them and use testdisk and photorec to recover files.

Please point me to some resources on where to get started if this is possible. 

```

# graid5 list
Geom name: data
State: COMPLETE CALM
Status: Total=3, Online=3
Type: AUTOMATIC
Pending: (wqp 0 // 0)
Stripesize: 65536
MemUse: 0 (msl 0)
Newest: -1
ID: 324261672
Providers:
1. Name: raid5/data
   Mediasize: 1500312633344 (1.4T)
   Sectorsize: 512
   Mode: r0w0e0
Consumers:
1. Name: ad10
   Mediasize: 750156374016 (699G)
   Sectorsize: 512
   Mode: r1w1e1
   DiskNo: 2
   Error: No
2. Name: ad6
   Mediasize: 750156374016 (699G)
   Sectorsize: 512
   Mode: r1w1e1
   DiskNo: 1
   Error: No
3. Name: ad4
   Mediasize: 750156374016 (699G)
   Sectorsize: 512
   Mode: r1w1e1
   DiskNo: 0
   Error: No

# graid5 status
      Name         Status  Components
raid5/data  COMPLETE CALM  ad10
                           ad6
                           ad4
#

```

I would appreciate any help that can be given in this matter.

If any more information is needed please let me know.

Side Note:
I already tried using a bunch of FreeBSD live CD's but the system will not boot them but Ubuntu Live CD will. I know Linux better anyway and would like to use that instead. The FreeBSD forum has been of no help. I have gotten no responses.

~Aaron J Smith

---

### Post by tgalati4 on 2013-01-23
So you have a freenas system that failed in some fashion and you can boot the system in Ubuntu.

So you know that the system is bootable in some fashion.  Can you put freenas or [http://nas4free.org](http://nas4free.org) on a USB stick and boot?  I would think that getting freenas or nas4free working is a top priority.  I don't think you will have much luck trying to read (possibly damaged) UFS drives in Ubuntu.  You could try PCBSD.  I don't know if a testdisk/photorec tool exists in PCBSD. (I'm guessing that it does because testdisk can read and possibly repair UFS drives.) 

How did the freenas system fail?

---

### Post by aaronjsmith21 on 2013-01-23
Sorry, I guess I did not mention that the FreeNAS system is still functioning.

Full issue:
My Drives got deleted out of the Geom Raid5 Configuration and the GPT got deleted or became unreadable some how on accident so I had to go through many steps just to get the Raid Set back up and out of rush to set the disks back up via the CLI (Which took me months to figure out) I ended up running the command newfs (plain and simple I knew what it did and was not thinking, a duh moment when you are just reading a post and doing what it says), which I canceled immediately  (CTRL+C) so now it reads as empty even through much checking online that newfs does not erase data it works just like deleting a file but until it is overwritten the data still is there. 

So now I need to run a rescue program of some sort to recover my files from it and TestDisk and PhotoRec are avalible via Ports on FreeBSD but I am not sure about PCBSD which is FreeBSD derivative so it might be. I will have to check into that.

The only thing I could find in my search about Geom was this page:
[http://manpages.ubuntu.com/manpages/hardy/man4/geom.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/geom.4.html)
Which says it can load geom classes, but I need it to load the raid5 class and not sure if it does or even where to start on installing it.

[S]Also, for anyone that needs to know, I can not load anything onto the FreeNAS system which is FreeBSD based because it is a bare-bone interface. So no option to install TestDisk or PhotoRec on it, also it is back from 2008 so not sure if it could be anyway, as it is build on version 6.2 of FreeBSD.[/S] - edit based on tgalati4's post that it was possible - left for reference 

I also do not want to keep the FreeNAS system or even use FreeBSD anymore at all as the user-base is very small and they are not quick to help when there is a problem, my posts have been on their forums for to long to be ignored, so I refuse to stick with them. I want to move my Network Storage to Debian or Ubuntu Server as I have worked on them for many many years now.

~Aaron J Smith

---

### Post by aaronjsmith21 on 2013-01-23
And sorry,
Thank you @tgalati4 for the quick response.

Also, some additional info, I did a lot of research on why FreeBSD will not boot is do to some odd BTX Loader issue they have that will fail or error out during the load of some SATA and/or RAID Controllers (in my case a Promise PCI PDC40718 SATA300 controller card), mostly Promise and NVIDIA. It either will display and error message dump or in my case, keep rebooting the system over and over, which is odd, I am wondering why FreeNAS installed in the first place but maybe it did not use BTX Loader? Or that it is based on a much older version of FreeBSD? At this point I don't care, *GRIN*, you would think this would not be an issue in later releases.

---

### Post by tgalati4 on 2013-01-23
I run freenas 7.2 and if you install it to a hard disk (as opposed to USB/ramdisk) you can load just about any bsd package.  So I would load the latest pcbsd and use the tools available.  I'm pretty sure testdisk is built for bsd since the man page in linux says it supports ufs.

The fact that you did a partial erase/reformat of the disk is going to make testdisk restoration virtually impossible.  Photorec should be able to recover files that are chain-linked, but recreating the partition table and the raid set will be close to zero.  Good luck.

---

### Post by aaronjsmith21 on 2013-01-23
Thanks again, and I will be testing out PCBSD.
Well, I guess that throws testdisk out the window, which I should have assumed as I had re-created the partition table, so oops. ;) Ya, that was a total "my bad". I guess I am down to just recovering the files via PhotoRec and look for some other programs that may work also.

I think if I ran the testdisk it would show I already have a valid partition table so you are probably right.

---

### Post by aaronjsmith21 on 2013-01-23
Holy Schnikes, I am able to install FreeBSD packages, even from the Web Interface. 
Wow, wish I knew that a long time ago, would have saved me months of work.
Now to see if I can get a PhotoRec package for FreeBSD 6.2. 

Thank you so much in pointing something out that I did not see a long time ago... 

I may have to install make and other stuff first not sure...

---

### Post by tgalati4 on 2013-01-23
You can pretty much add as much as you want with freenas.  It just starts out as barebones, because it's just a NAS, but many folks add services and end up turning it into a headless pcbsd distro--with a web-based gui.  The philosphy is that reliabilty would go down if you run a lot of stuff and zfs requires a lot of RAM and CPU horsepower which gets used if you are running a bunch of other services.

I've been pretty happy with the reliabilty of 7.2 over the past few years.  8.3 requires much newer hardware, but 7.2 has now been forked/redirected to nas4free to keep the old-style freenas going.

File recovery is no fun.  Nor are backups, but you have to do one or the other.

---

### Post by aaronjsmith21 on 2013-01-24
I felt I should add some reference information to how I solved my data recovery problem on my FreeNAS system thanks to tgalati4.

I am running:
[U]FreeNAS 0.686.3 (revision 3011)
built on Thu Mar 13 19:20:49 CET 2008[/U]
Platform: 
_FreeBSD 6.2-RELEASE-p11 (revision 19950_6)
With:
_GEOM raid5 (graid5)_

Process of installing packages on FreeNAS system with internet connection:
```
pkg_add -r package_name
```

FTP connection problems in later FreeBSD Releses due to archived ftp resolution:
Find you version of FreeBSD on this list:
For i386 systems:
[http://ftp-archive.freebsd.org/pub/FreeBSD-Archive/old-releases/i386/](http://ftp-archive.freebsd.org/pub/FreeBSD-Archive/old-releases/i386/)
For 64-bit systems:
[http://ftp-archive.freebsd.org/pub/FreeBSD-Archive/old-releases/amd64/](http://ftp-archive.freebsd.org/pub/FreeBSD-Archive/old-releases/amd64/)

From the ssh or cli of the system you need to run:
```
setenv PACKAGESITE the_ftp_package_location
```

It will look similar to:
```
setenv PACKAGESITE http://ftp-archive.freebsd.org/pub/FreeBSD-Archive/old-releases/i386/6.2-RELEASE/packages/Latest/
```

So from the above list location you need to copy the link to your FreeBSD version + /packages/Latest/ or you could just browse to that location on the site and copy the full link.

**NOTE:** This will only work for that session alone you have open, restart or closing the ssh connection or opening a new one will not keep this environment variable set so it will revert to the old ftp site. You may need to look up how to make it permanent, I had no need so not sure, probably is easy.

Packages I installed to try and recover data:
```
pkg_add -r testdisk
pkg_add -r magicrescue
```

You may have to use full directory path to use these files as they are not on the path list.
On my system:
testdisk and photorec installed in /usr/local/sbin/
magicrescue installed in /usr/local/bin/

and in needed to install jpeg-mmx and mpg123 for magicrescue to work << as far as I know, could need more, have not gotten that far.

Other Programs I found that could help:
SleuthKit:
[http://www.freshports.org/sysutils/sleuthkit/](http://www.freshports.org/sysutils/sleuthkit/) by [http://www.sleuthkit.org/](http://www.sleuthkit.org/)
FFS2Recov:
[http://www.freshports.org/sysutils/ffs2recov/](http://www.freshports.org/sysutils/ffs2recov/)

I strongly recommend working from a disk image of your filesystem before running any of these programs, a drive big enough to hold the complete disk image copy of your setup and make a copy of it using dd:
For my setup I had a 1.4 TB raid5 setup so I needed at least that much space to copy to so a 2 TB drive works.
I ran:
```
dd if=/dev/raid5/data of=/mnt/2tbdrive/raid5.bak.img bs=1m
```
the "if" or input file is that of the device you want to copy, all your devices should be listed in /dev/ somewhere and you should really know what you are doing here.
the "of" or output file is where you want to copy it to and make sure that place has enough free space to handle the size of the file system.
the "bs" or block size is set to 1mb (1024kb) on my copy

then you can run any of those programs against the disk image instead of on the actual drive and not mess anything up.

That's my current story. I hope this helps anyone who may come across this in the future...

~Aaron J Smith

---

### Post by tgalati4 on 2013-01-24
An impressive tutorial.  Thanks for your contribution.  This needs to be put in the nas4free wiki.

---

### Post by johnny12 on 2013-12-14
[COLOR=#000000]aaronjsmith21[/COLOR]

[COLOR=#000000]Thank you for your post.  My situation is about the same as yours.  Tomorrow I will go through the steps that you recommended, but was wondering if you would be willing to help me out if I run into any snags.  It sounds like you and  tgalati4 have some good experience with this.

I have gotten to that point where I am willing to send the HDDs to a Data Recovery Service.  It is hard to work on them, because every step that I take that does not work out makes it even more disappointing. 

Here is my post on a different form - [/COLOR][http://forums.nas4free.org/viewtopic.php?f=65&t=1762.](http://forums.nas4free.org/viewtopic.php?f=65&t=1762.) 

J

---

