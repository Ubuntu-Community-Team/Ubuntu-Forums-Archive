---
title: "DMA activation for CD/DVD ROM Drive"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by bigjack on 2007-07-24
In my attempt to improve the performance of the CD/DVD ROM drive, I have been trying to set up DMA as per the Community Doc "DMA." ([https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)).  I also have read through previous threads that appear to be similar to this problem.  Unfortunately, some of the previous threads were never resolved.

I first went to
System => Administration => Services  and made sure both DMA and hdparm are on.  Rebooted.

When looked for /dev/hdc with 
sudo hdparm /dev/hdc
the response was:
/dev/hdc: No such file or directory

By looking in /dev I found cdrom, dvd, and scd0.  The responses when checking with sudo hdparm for each were:

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

/dev/dvd:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

So tried to set DMA of scd0 with
sudo hdparm -d1 /dev/scd0
but received the following

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

When sudo hdparm -d1 -k1 /dev/scd0.  The response was

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 setting keep_settings to 1 (on)
 HDIO_SET_KEEPSETTINGS failed: Inappropriate ioctl for device

I've edited /etc/hdparm.conf to include

/dev/scd0 {
dma = on
}

rebooted, but get the same response when I ran
sudo hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

I looked at /etc/modules, but there is no ide-cd to put the suggested
piix
ide-core
above, so I put in a line ide-cd.  Actually tried all possible combinations with ide-cd alone, ide-cd with piix etc, and piix ide-core w/o ide-cd.  Keep getting same message:  HDIO_GETGEO failed: Inappropriate ioctl for device.

Here is what is returned when checking with ls -l /dev/scd0:
brw-rw---- 1 root cdrom 11, 0 2007-07-24 14:45 /dev/scd0

What should permissions be?

What do I do next?

____
IBM ThinkPad T40, 512 Mb RAM, Feisty 7.04

---

### Post by iox on 2007-07-28
Hi! I have exactly the same problem (same commands - same output!)

I'm  trying to activate DMA because I'm having problems burning CDs with Feisty.

I'll keep you informed if I find out anything new :)

---

### Post by MrHippocampus on 2007-07-28
Since the drives are coming up as scd* rather than hd*, that means your using the libata driver or your using a SATA cd drive. In either case hdparm wont work as its designed to be used on hd* devices, since there coming up as scd* devices they *should* be auto-configured for optimum settings. Im not sure if theres a way to check/change those settings though :(

---

### Post by jdk_ on 2007-07-28
Same troubles here, The question remains the same: what could we do about it?

---

### Post by bigjack on 2007-07-29
I don't understand why someone hasn't figured out that this is a real problem with Linux in general.  After doing some more internet searches, I discovered that this problem as been around for several years.  It might have to do with a problem in the kernel itself (see near the end of this post).

I have been using Ubuntu Linux for several years.  Was using 7.04 (Feisty) for about 6 months, but reinstalled 6.10 (Edgy) because for some reason, my IBM ThinkPad T40 runs faster with it.  I also have installed and tried Fedora Core 7, Mandriva, Linspire, and openSUSE 10.2.  All distributions were installed through CDs (i.e., the CD/DVD drive works when not accessed through Linux).  For the IBM ThinkPad T40, Ubuntu 6.10 (Edgy) appears to be the best overall.

There is a problem with Edgy as well as with Feisty and the other Linux distributions I have tried:  The CD/DVD ROM does not work consistently--many CDs and DVDs do not open.  All that happens is a click click coming from the CD/DVD-ROM drive.  The problem is not codecs:  All codecs for playing DVDs and CDs have been added from the various repositories.

When I check hdparm with "sudo hdparm /dev/hdc" the result is:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

In Feisty, hcd was replaced by scd0, but results were the same.

When I searched various Linux forums for help with the "Inappropriate ioctl . . ." problem, I was able to see that others have had the problem, but that no forum directly answered how to fix the problem.  I came across the cdrom.h file through a search for commands in Unixx.

What can be done to correct this problem?
HDIO_GETGEO failed: Inappropriate ioctl for device

It possibly has to due with cdrom.h in the kernel.

/usr/src/linux-headers-2.6.17-10-generic/include/linux/cdrom.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/sc6600/cdrom.h
/usr/src/linux-headers-2.6.17-10/include/linux/cdrom.h
/usr/src/linux-headers-2.6.17-12-generic/include/linux/cdrom.h
/usr/src/linux-headers-2.6.17-12-generic/include/config/sc6600/cdrom.h
/usr/src/linux-headers-2.6.17-12/include/linux/cdrom.h

I am a novice to computer programming but can follow clear and concise directions.  Anyone out there know how to modify cdrom.h so that CD/DVD ROMS (and possibly burners) work?

I've added this to a similar thread.  These threads should be combined and someone who knows something about cdrom.h contribute to solving the problem.

---

### Post by gottferdamnt on 2007-07-30
Same issue on my laptop :/

---

### Post by ril560 on 2007-09-26
Anyone come up with anything?

---

### Post by jts on 2007-10-13
Ditto. One of my drives is now doing a buffered read at 1MB/sec!

---

### Post by jts on 2007-10-18
Still nothing.  I had read that it would be fixed in Gutsy.  Running gutsy now and it still fails.

---

### Post by ethana2 on 2007-10-21
Toshiba Satellite.

Ubuntu Gutsy --upgraded from Ubuntu Studio Feisty.

Appears to have same problem.  Innapropriate ioctl's for the device, and failed read and write with hdparm.  Drive succesfully reads data disc, and we have, though horrible laggily/choppily, watched a DVD on our system.
How many launchpad tickets have been filed on this issue?  Give them my vote.

My dad is trying to fix this problem by reinstalling his windows sound drivers.  I'd like to beat him to the punch with a simple software update.

---

### Post by viral_sonata on 2007-10-29
Add one more frustrated user to this list.  Finally made the plunge and have been rewarded with non working burner and my sata hd being invisible.  Although the burner is sata as well so may be same issue.  Oh, on a fresh install of Gutsy.

---

### Post by sokairyk on 2007-11-14
I also get those outputs and I'm running a fresh Gutsy install...

I came across those commands wile I was searching for a problem I have with k3b. I don't know the consequences for such readings but I have some discs that only list the files and read -1 for owner group and unknown permissions.

Besides that (I get it only for 3 specific discs) when I try to copy a DVD from one drive to another with k3b growisofs and k3b get unstable and load my CPU at 100%.

If I choose to create an image of the disc first k3b hangs when the disc burning starts but the device is working properly and it copies the disc (just doesn't eject it).
{When I installed kde-core this problem was fixed.... I think....}

If I copy the disc on the fly it hangs at 99% and never finishes the disc. The DVD reads empty?!?!?

On both occasions I have to either kill k3b and growisofs is also killed. If I kill growisofs first it changes its state to zombie and ends only if I kill k3b. Although in System Monitor growisofs is listed as one process, when I run "ps -A|grep growisofs" it lists 4 processes with the same PID?!?!?!?

gnomebaker which also uses growisofs gives me no problems but does not compaire to k3b....

I don't know if this is relevant to DMA but I would appreciate any suggestions.

---

### Post by sagui on 2007-11-14
Same exact problem here too.

I tried a bunch of Distros to see if it's K/Ubuntu specific problem but it isn't.  Fedora 8, PCLinuxOS, Freespire, OpenSuse 10.3 all have the same issue.

I'm now dual booting Gutsy with MEPIS (Dapper based distro).  Annoying as hell, but I need my burner.

---

### Post by ximian on 2007-11-24
Ok so,i have been trying very hard to figure this out for myself.Setting up DMA on a disc that is labeled as /dev/scd0.Now anyone here already knows that hdparm in no way shape or form can be used to enable DMA on a sata or scsi disc,only on scsi emulated discs.In Gutsy i have found that for some strange reason way before hdparm's update through ubuntu,they decided to setup CD/DVD reader/writers as some sort of scsi,yet not an easy scsi emulation,but something totally different,which inturn makes my disc seen as /dev/sdc0.So did alot of Google and anything else on the linux websites for help from anyone who can help,and so far have only found  workarounds/fixes that envolves everything from recompiling kernels to reestablishing how your computer sees your CD/DVD at bootup by appending combined_mode=libata to the kernel line in GRUB,haven't tried any of it,still a n00b,just thought i might share a bit of info.

Ok so here's the links,hopefully this helps someone out there,until a better fix happens,i feel i will leave all my burning and dvding to my Vista partition.

 [http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive)
[http://www.fedoraforum.org/forum/showthread.php?t=114586](http://www.fedoraforum.org/forum/showthread.php?t=114586) 
[http://www.serpentine.com/blog/2006/12/12/make-linux-happy-with-a-modern-laptops-cddvd-drive/](http://www.serpentine.com/blog/2006/12/12/make-linux-happy-with-a-modern-laptops-cddvd-drive/)

:confused:Note:Eventhough this a Fedora Forum,it did answer some of the questions that i had as to why one ,i was not able to enable DMA using hdparm -d1 /dev/scd0,and two why hdparm needs to be updated,because sdparm doesn't work either.My drive is a physical IDE not SATA,so in theory hdparm should work,but doesn't.Hopefully we will find some sort of a solution,using windblows is killing my opinion of Ubuntu.Burning cd's and dvd's and watching dvd's without any type of freezing or jerkiness is very important,atleast to me.:(


PS:What the heck is PATA and why do we even need it???It's the root of the evil in this world......

---

### Post by sagui on 2007-11-27
> **ximian said:**
> 
[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive)
[http://www.fedoraforum.org/forum/showthread.php?t=114586](http://www.fedoraforum.org/forum/showthread.php?t=114586) 
[http://www.serpentine.com/blog/2006/12/12/make-linux-happy-with-a-modern-laptops-cddvd-drive/](http://www.serpentine.com/blog/2006/12/12/make-linux-happy-with-a-modern-laptops-cddvd-drive/)


Thanks for those, reading those pages, I started to realize that my problem was something else.  See i have a new laptop, one that actually has a SCSI drive, so the interferences described above do not concern me.

So since I figured that out, I thought that maybe my problem was something else, so I kept looking around.  Finally I found a thread somewhere that suggested using an option with burnfree, so i selected TAO instead of DAO in K3B and tadaaaa!!!  Burned a non-coaster for once.

Hope you guys get it figured out!

---

