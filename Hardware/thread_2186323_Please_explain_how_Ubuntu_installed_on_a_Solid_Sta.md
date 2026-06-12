---
title: "Please explain how Ubuntu installed on a Solid State Drive with Logical Volume Mgmt?"
date: 2013-11-06
forum: Hardware
---

### Post by bc9 on 2013-11-06
Hi, I'm moving from an old PC running Ubuntu 10.04LTS (which I love) to a slightly-less-old PC on which I just installed Ubuntu 13.04 (which I suppose I'll get used to). Since I'm setting up a 'new' PC w/13.04 I treated myself to my first SSD (solid state drive, a 120GB Kingston from Newegg for $79.). Installing the SSD as the boot/system drive went fine, as did the 13.04 install from to it from DVD. At the moment, the 120GB SSD is the ONLY DRIVE in the machine, not counting the empty optical drive tray and empty card readers.

I look at Disks and I'm a bit confuzzled. It seems to show more than just the single 120GB SSD installed... but I'm probably not understanding what it's showing me and was hoping someone could clarify.

System Monitor/File Systems looks pretty much like I'd expect: a couple of partitions that add up to about 120GB total size. The main one "/" is ext4 and the little one "/boot" is ext2 (I didn't specify the types, so I guess those are defaults). 

What Disks shows has me scratching my noggin: sure, the 120GB Kingston SSD shows up at the top of the list of Disk Drives like I'd expect, though there are two Other Devices listed ALSO... one is root and one is swap and they add up to roughly 120GB which seems to make sense (these are partitions on the SSD that Ubuntu made during formatting/installation I assume)? However, when I select the 120GB Disk, the graphic SEEMS to show a 255MB ext2 partition that contains TWO other partitions, each of which is 120GB in size (the bottom one, called 'Partition 5' has the words "LVM2 PV" after "120 GB" ...I'm guessing that refers to the Logical Volume Management checkbox I clicked during install.

So, you can see my confusion. Normally, I'd expect to see a single roughly 120GB drive and have expected Ubuntu to have divided it into a couple of partitions (the smaller one for swap) and that's it. Now I look at Disks and I'm not sure I understand it (here's a screen cap of what I see: [http://imgur.com/syUbVRF](http://imgur.com/syUbVRF) ). 

[[IMG]http://i.imgur.com/syUbVRF.jpg[/IMG]]("http://imgur.com/syUbVRF")

Could someone please explain to me why it looks as it does? Should I *NOT* have clicked that Logical Volume Management checkbox during install? I only did because it said it made resizing partitions easier, which seemed like a good thing. Should I just go back and re-format/re-install WITHOUT LVM? Is it even necessary?

BTW, if you're feeling extra charitable, maybe you could let me know about that thing where too big a chunk of every drive is held aside for swap... even on data-only drives that presumably don't need such swap space? I recall looking into that four years ago when I saw how much space was made unavailable because of that... and the fix (to reduce the swap percentage?) looked complex/wasn't even clear if it could be applied to drives with data already on them. Anyway, I just learned to live with the lost drive space, and hoped this would be fixed in later versions of the OS, but am not sure whether it has been addressed. Any info/links about this (as it applies to Ubuntu 13.04 with or without LVM) would be appreciated. 

Thanks! :)

---

### Post by dragonfly41 on 2013-11-07
> 
Should I *NOT* have clicked that Logical Volume Management checkbox  during install? I only did because it said it made resizing partitions  easier, which seemed like a good thing. Should I just go back and  re-format/re-install WITHOUT LVM? Is it even necessary?


I second that question since I made the same mistake of selecting LVM when I recently installed Ubuntu 12.04 server on an old Sony PC.  Now I can't resize the partition .. and I read that this choice of LVM made resizing partitions easier!

If you install GParted (Software Ubuntu Centre) and launch Applications > System Tools > Administration > Gparted Partition Editor ... do you have a red warning flag against /dev/sda5?

My installation reads .. "Logical Volume Management is not yet supported" ... and I'm not sure if this just means that LVM is not supported in GParted.

I would like to go back to "non LVM mode" (learning from this mistake) but it seems that this requires a reinstallation.

---

### Post by bc9 on 2013-11-07
Hi Dragonfly41 and thanks for your reply.

I've never heard of or used GParted, so I can't answer your question about the red flag warning atm (I'm using the old PC w/10.04LTS atm). 

I suppose I should have read about LVM before I clicked OK during the install... all the installer said was that sentence about making 'snapshots' and 'partition resizing' easier so I figured 'why not?' 

I don't even know whether anything's amiss... I could just be reading the 'Disks' info incorrectly. Then again, I generally have no need to resize partitions once they're made and (assuming 'snapshots' means making backups) I do my backing up manually (click-and-drag to an external drive). So, maybe I *should* go ahead and just reinstall Ubuntu 13.04 over again without LVM and see what happens... better to do that now (before I've moved all my stuff to the new PC and got it set up how I like) than later. If I do, and things look different, I'll reply here to let you know.

If anyone can explain to me why I see what I see in Disks, I'd still appreciate the edumacation. ;-)

---

### Post by steeldriver on 2013-11-07
I don't really use the 'Disks' utility (I'm more familiar with command line tools), but I don't see anything wrong with what it's reporting

You have a single physical disk (sda - your SSD) that has a primary boot partition (sda1) plus an extended partition (sda2) in which there is a single logical partition (sda5). So far no surprises - this is a fairly normal choice for a disk using the older MBR partition table type (which is limited to 4 primary partitions - creating an extended partition right off the bat gives a bit more flexibility to subdivide the disk in the case when you're NOT using LVM on top). Note that sda5 is a logical division within sda2 i.e. they are the same physical disk blocks (it is NOT showing 2 x 120GB 'disks').

Then the sda5 logical partition becomes a physical volume (PV) within your LVM. The installer has created a swap volume of 8.6GB (presumably based on the detected amount of RAM - you need swap size at least equal to RAM in order to suspend) and allocated the remainder as a single logical root volume.

---

### Post by dragonfly41 on 2013-11-07
I've been researching/learning further about LVM and this
blog sheds more light on the subject ...

[http://pubmem.wordpress.com/2010/09/16/how-to-resize-lvm-logical-volumes-with-ext4-as-filesystem/](http://pubmem.wordpress.com/2010/09/16/how-to-resize-lvm-logical-volumes-with-ext4-as-filesystem/)

Also in Ubuntu Software Centre ... install Logical Volume Management
which provides a GUI for managing LVM.   Note the warning about use with RAID.

I think that the warning message in GParted simply means that GParted does not support LVM.

So I intend to play around with this to learn more about the benefits of LVM.

[Later edit]

Another thread found below which is relevant ...

Apparently this is why I saw an error message with Ubuntu 12.04 + LVM ...

> 
Only the latest version of Gparted (0.14) supports resizing LVM physical volumes. The version that ships with Ubuntu 12.10 or 13.04 does not support it.


[URL="http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume"][http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)

[/URL]

---

### Post by oldfred on 2013-11-07
You chose full disk encryption and that uses LVM. While LVM makes it easier to resize partitions if you are LVM familiar, but I find gparted easier since it is a nice gui.
With LVM, you have a separate /boot and swap as well as the full LVM with then can have additional logical partitions inside the physical partition.

Unless you really need or want encryption, I would not suggest LVM unless familiar with Linux and partitioning with LVM. Also since encrypted you need really good backup procedures as any drive issue may not be recoverable as standard tools will not be able to recover data. Or the reason for encryption is to prevent anything from reading your drive without your passphrase.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

---

### Post by 1clue on 2013-11-07
The biggest thing about using an SSD is you should mount its partitions with the 'noatime' option.  This turns off access time.  By default, Linux records the last time a file was accessed every time you access it.  It's handy, but each time it does that it's a write to your disk.  That's bad for a device with a limited number of writes.

The second thing I'd like to mention is that if you figure out how to use it properly, LVM is a wonderful thing.  I don't much like the way Ubuntu does it by default, though.

The third thing is I'd like to rail against DOS/MBR partition tables.  This is the all-too-familiar partition table with a maximum of four primary partitions, one of which could be "extended" which gives you a bunch of others as options.

<rant>
What a lot of people don't understand is that this partition table became obsolete when storage units reached 32 megabytes.  Yes, megabytes.  It's been extended twice, first to 128m, and the latest limit is a 2T disk size max.  There are only 256 possible partition types, which is not enough to define all the partition types currently in use in computing.

If you have a non-EUFI box and a Windows dual-boot, then you might still need a DOS partition table. If you use only Linux and have newer hardware, then  IMO there is no valid reason to use this dinosaur.  You should use GPT partition tables.

GPT has no need of extended partitions, you get up to 128 partitions, a maximum storage size which is large enough to be unlimited in any practical sense, and a backup of the partition table in the event of an accident.  And an unlimited number of partition types.  And quite a few other advantages.

That said, Ubuntu's installers don't use it.  For some reason I can't fathom.

</rant>

---

### Post by oldfred on 2013-11-07
I also like gpt partitioning. I have used it since 10.10 with Ubuntu and have two drives and even a flash drive with gpt partitioning.
Ubuntu will work with gpt, but because Windows only boots from gpt partitioned drive with UEFI, the default still seems to be MBR partitioning.
Somewhere about 1.5TB drives that are blank will be partitioned with gpt by the Ubuntu installer. But most drives have partitions already so it uses whatever it finds. 
I normally partition in advance with gparted and change default from msdos(MBR) to gpt under device, advanced settings.

---

### Post by djsephiroth on 2013-11-07
> **dragonfly41 said:**
> I read that this choice of LVM made resizing partitions easier!

I would like to go back to "non LVM mode" (learning from this mistake) but it seems that this requires a reinstallation.

It does, to both of those. LVM allows you to make an arbitrarily huge number of partitions, and each partition can sit on top of part of a drive, one drive, several drives, several parts of several drives...
GParted, fdisk, etc. work with the physical disk. LVM is a logical layer above the physical disks, so of course those tools will not help you - they're looking at the wrong layer!
If you look at pvcreate, lvextend, and the other LVM tools, you'll have what you need to resize LVM stuff.

If you want to get rid of LVM, you will be getting rid of the logical partitions your current filesystems are on, so yes, you will need to reinstall (or at least dd your LVM filesystems to physical ones and edit the files that control booting and mounting partitions).

> **bc9 said:**
> 

Could someone please explain to me why it looks as it does?

The disk utility is showing you several layers of abstraction, draped over one drive. At the lowest layer, you have the full 120GB SSD. Above that, you have partitions of 111GB and 9GB. The 9GB is your swap. The 111GB partition is itself partitioned into even smaller LVM partitions. Put another way, your /home, /, /tmp, etc. are on LVM logical partitions, which are inside that 111GB physical partition.

Here's an example of how you might be presented with multiple levels of the same physical device:

[ Raw Physical Disk 100 GB] 100 = 100
[ /boot 1GB ] [Encrypted Partition 90GB ] [Swap Partition 9GB] 1 + 90 + 9 = 100
[LVM / 40GB ] [LVM /home 50GB] 1 + (40 + 50) + 9 = 100

So you have, say, a 100GB HDD.
This HDD is partitioned into a boot partition, a swap partition, and an encrypted partition.
The encrypted partition is then sliced up by LVM into yet another layer of partitions.
... and you can mount those partitions as, say, /home (your stuff) and / (everything else)

Why on earth would anyone use so much complexity? You get around the MBR partition limits. You can add more space to existing partitions while you are using them, and that space can some from any other layer - a physical drive, a partition of a physical drive, a RAID, whatever. Also, you don't have to use partitioning tools. Just a few commands of pvcreate, vgextend, and lvextend, and bam, your /home partition is magically bigger.

This isn't a thing you really need unless you see yourself using multiple hard drives and extending your existing partitions over those drives; but it's very useful if that's what you need to do (for example, a production server that needs more disk space on /var, but can't be taken offline).

> **oldfred said:**
> You chose full disk encryption and that uses LVM.
I didn't see the encrypted volume in the OP's screenshot. It looks like LVM is using a non-swap partition of the raw disk as the underlying volume, not an encrypted partition. Does the graphical installer only offer encryption + LVM, or can you choose one or the other? I use the alternate installer, so I may be out of touch.

If OP's chosen full disk encryption, that means LUKS, which means serious wear on the drive.  

> **1clue said:**
> 
<rant>
MBR bad, GPT good
That said, Ubuntu's installers don't use it.  For some reason I can't fathom.
</rant>
Compatibility.

You can use LVM on top of LUKS on top of RAID with GPT disks, if you want (I do). Just don't use the default "one size fits most" installer, or alt-F2 into a shell during install and set things up the way you like them. Such is the joy of FOSS.

---

### Post by oldfred on 2013-11-07
I guess I assumed encryption. There is also a LVM option.

See attached.

---

### Post by mörgæs on 2013-11-07
> **bc9 said:**
> ... on which I just installed Ubuntu 13.04 

Are you aware that support for 13.04 is only a couple of months more?

---

### Post by bc9 on 2013-11-07
THANKS everyone for the feedback. :-) Some of what's been described is beyond my experience level... though I've got 25+ years with computers, only the past few with PCs and Linux. 


dragonfly41: I don't know that I even need LVM or what it provides, so I'll probably just go back and reinstall 13.04 without it. Thanks for the links to other threads... more bedtime reading for me. ;-)


steeldriver: I'm not sure I follow all of what you're saying but defer to your opinion that Disks is reporting what it should. It *looks* like two partitions of 120 GB each to me, but I'm happy to take your word for it. I only used Disks because it's what was available immediately after installing the OS. My PC has 8GB of RAM by the way, which I assume is why the swap got sized as it did.


oldfred: I specifically recall NOT choosing to encrypt the disk during installation... the ONLY checkbox I clicked was the one about LVM and left the encryption one UNchecked... so maybe LVM uses encryption by default? I generally never choose to encrypt stuff (my PC is at home and I'm the only one who uses it, so just a login password seems enough).


1clue, etc...: This is my first SSD ever and only my second computer running Ubuntu (I'm an enthusiastic convert from MacOS). Unless it's part of some custom install option, I don't remember seeing ANYthing about having partitions on the SSD mount with the 'noatime' option. Based on what you say, it seems like it'd be a good idea to do as you suggest... but since it's the operating system partition on the SSD that boots the PC itself, I'm not sure how I make it mount with 'noatime' ...is that something I can change AFTER it boots so that it'll boot that way from that point on? Similarly: re: the DOS/MBR partition tables you dislike: can I avoid that? Pardon my not knowing more about those things.


djsephiroth: thank you (!) for the clarification re: Disks. I want to AVOID complexity whenever possible. 


morgaes: everything gets replaced eventually. I did think of waiting til the next long term support release (14?) but as my old PC is on its last legs, letting the new (used) one sit around til then seemed ill-advised. I expect I'll upgrade to the next LTS release when it's available and leave it like that for years... I was VERY happy with 10.04 LTS and ignored Ubuntu 11 and 12. 

[SIZE=3]**TO ALL: I don't need encryption, LVMs, the ability to have many different partitions or resize them later. Nor do I need RAID, dual booted operating systems, or anthing else like that. I'm happy to use ALL of the SSD just for Ubuntu and programs... I just want it to work smoothly/efficiently and be durable (avoiding needless extra writes to the SSD).**[/SIZE]


I use the PC to do work, not to have something to work on ;-). It's an early i7 box with an Intel DX58SO logic board with 8GB of RAM.


[SIZE=3]**I simply want to install Ubuntu 13.04 on the SSD in the most simple/sensible manner... so that it runs as fast as it can on the SSD and the PC. Some of what's been mentioned above didn't even seem to be options to choose in the regular installer (the one you use from the downloaded/burned iso DVD). I'm happy to re-install without LVM. BEFORE I do, is there ANYTHING else that I can or should specify re: 'noatime', DOS/MBR partition tables, KUKS, etc... (or do I take care of 'noatime' etc... after installation?)**[/SIZE]


**THANKS again** to everyone for the help. Please pardon my being newish to some of these things. :-)

---

### Post by oldfred on 2013-11-07
Yes, just LVM without encryption is an option as I posted above.

If you just want a total simple install you use the erase disk which will totally erase entire drive not just a partition. But I normally suggest a smaller / (root) partition of 10 to 25GB, a 2GB swap at end of drive and everything in the middle as /home. But to do that you have to use manual install or Something else. Only if hibernating would you need swap equal to RAM in GiB not GB.

I do recommend gpt, but many do not know what it is. And MBR(msdos) has been around since the beginning of time (PC computers that is). But to get gpt you have to manually partition in advance and still use Something else to choose partition's mount points and formats. May be easier to stay with MBR. We can give details on either if you specify.

You can change most settings after your install to reduce writes to SSD. Some now say with the new SSDs that even the changes we often suggest are not really required as the life of an SSD will not really be any different than that of a hard drive.

This is how I partitioned my SSD, but I had planned on moving it to a new system that would be UEFI so I also included an efi partition at beginning of drive. I have two / (root) partitions, one current and one for testing future that will soon be 14.04. All my data is on my rotating drive.

```
fred@fred-Precise:~$ sudo parted /dev/sde unit s print
[sudo] password for fred: 
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sde: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal

```

I used ext4 for format but then turned off journalling to reduce writes. If I happen to have corruption that fsck cannot fix, it is just my Ubuntu system and I can just reinstall. Only a few settings and a list of installed apps would I need & I back those up.

---

### Post by 1clue on 2013-11-07
bc9,

First, noatime:  It's an option for mounting partitions in the Linux kernel.  You edit your /etc/fstab and alter the partitions which reside on your ssd:

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=66a4b4cb-ba2b-4911-ae5f-9fcd86637917 /            ext4  **noatime**,errors=remount-ro 0 1 #/dev/mapper/sddvg1-host_root
UUID=3508c843-17d7-4c5b-9adc-33dfe6fe9f8d /boot        ext2  defaults                  0 2 #/dev/sda1 during installation
UUID=ce3ee06b-f9c9-44eb-a1b9-102870c6a587 /archives    xfs   defaults,user             0 0 # removable
UUID=d91d72c6-ef60-4345-982c-23e34ae29949 /spinner     xfs   defaults                  0 2 #/dev/mapper/hddvg1-host_spinner
UUID=b589e0a1-dbdb-4c51-8ec5-9fa1b5217314 none         swap  sw                        0 0 #/dev/mapper/hddvg1-host_swap

```

BTW, the only partition which is NOT on LVM is the /boot partition.

Then just FYI I have this sort of thing for my logical volumes:
```

  LV             VG     Attr     LSize   Pool Origin Data%  Move Log Copy%  Convert
  host_spinner   hddvg1 -wi-ao-- 153.13g                                           
  host_swap      hddvg1 -wi-ao--  22.35g                                           
  vmbbTrunk_swap hddvg1 -wi-a---   4.00g                                           
  vmcore_swap    hddvg1 -wi-ao--   4.00g                                           
  vmghbase_root  hddvg1 -wi-ao--  20.00g                                           
  vmghbase_swap  hddvg1 -wi-ao--   4.00g                                           
  vmus1204_swap  hddvg1 -wi-ao--   4.00g                                           
  y_root         hddvg1 -wi-a---  20.00g                                           
  z_root         hddvg1 -wi-a---   8.00g                                           
  freenas_files  rd1vg1 -wi-a--- 300.00g                                           
  vmus1204_root  rd1vg1 -wi-ao--   8.00g                                           
  host_root      ssdvg1 -wi-ao--  30.00g                                           
  vmbbTrunk_root ssdvg1 -wi-a---   8.00g                                           
  vmcore_root    ssdvg1 -wi-ao--   8.00g                                           
  vmghbase_root  ssdvg1 -wi-a---  20.00g                                           

```
You have to edit it with sudo, you can't do this as a normal user.

Now, you seem to be mixing things up. a bit.  It's not really that complicated.  With Linux/UN*X the tradition is for any tool to do exactly one thing really well.  It's this way with all these technologies:
[LIST=1]
[*]LVM is logical volume management.  It's a way to have a partition or groups of partitions be managed by an extra layer.  It lets you:
[LIST=1]
[*]resize partitions on the fly, including / partition, without shutting down or rebooting.
[*]Create new filesystems on-the-fly, mount them, maintain them.
[*]Have a volume group which spans multiple disks, move volumes from one disk to another etc.
[*]It makes an abstract storage space which does not depend on the limits of your physical hardware.
[*]It's really good if you use virtual machines or if you have a heavily used database.  And a lot of other things too, but that's what I use it for.
[*]It does NOT default to encryption.
[*]If you're looking at a simple system you don't really need it.
[*]The way Ubuntu installs it by default, I don't see how it can be all that useful.
[/LIST]

[*]Boot process:
[LIST=1]
[*]The first thing that loads is your kernel and a boot loader.  Basically the stuff in your /boot partition.  I'm leaving a lot out here but for a beginner who's probably got other things to think about, that's enough.
[*]The boot process loads the kernel and drivers, and starts scanning your disks for errors.
[*]Once that's done, it mounts the partitions as specified in /etc/fstab.
[*]This is where **noatime** comes into play.  It affects Linux and only Linux, and only the partitions for which it's specified, so if you were to have Windows it would have no affect on that.  Yes, I saw that you don't need Windows.
[/LIST]

[*]SSD hints:
[LIST=1]
[*]You should google on this.  *SSD Linux 2013* or *SSD Ubuntu 2013* will give you the latest advice for SSDs.  Or use whatever year your SSD was manufactured.  They're changing fairly rapidly in minor details, and the newer they are the better in terms of handling real operating systems.
[*]You want to maximize your RAM such that you never or almost never use swap except to hibernate.  Swap is heavy on writes, and it slows your system down a lot.  This is common sense on any storage technology, but it's much more critical on SSD.
[*]If you expect to use all your RAM, or if you are limited to 4g or less, you might want to add a spinning disk and put swap there.
[/LIST]

[*]GPT partition tables:
[LIST=1]
[*]As I understand your needs, there's no reason for you to NOT use GPT.  It's better in every way on recent hardware, and if you don't use Windows then there's really no excuse to stick with the dinosaur unless your hardware just doesn't support it.
[/LIST]
[/LIST]

---

### Post by dragonfly41 on 2013-11-08
One further point for consideration..

If I stay with current LVM option I  have setup without fully understanding the implications .. and in later times my disk crashes (I tend to recycle old,  sometimes vintage, devices) .. will [color=blue]testdisk,  photorec[/color] forensic tools still be able to recover data from LVM configured  drive?  Certainly not with encryption.

---

### Post by 1clue on 2013-11-08
I don't think you'll have any extra problems because of LVM.  It's been around for quite awhile, and it's pretty widespread.  If data recovery were more complicated I doubt it would be used.

Encryption:  I don't really see the advantage in using it.  If your system has enough information onboard to boot and mount the filesystems, then there's enough information to decrypt the data.  Any password you're likely to remember isn't going to give all that much additional security IMO, and any malware you inadvertently run will have access to your data anyway, since it's running as you under your session.

---

### Post by bc9 on 2013-11-08
Thanks again for the continued guidance. ;-)


oldfred, 1clue, etc...: 


Regular vs. manual install/partitions: I think I follow what you're saying but in the interests of simplicity, isn't /home *already* living in / (root)? So leaving it there (i.e.: just doing a 'regular' install (not manual) gives /home access to the same amount of room (assuming I'm using the whole SSD for Ubuntu, which I am)?


Tweaking things like 'noatime' after installation for SSD: years ago I used SGI Unix workstations daily for work and messed around with /etc/fstab, did scripting, etc... all the time. Of course, I haven't touched one of those machines in a decade, so have forgotten most of what I knew back then. Though my SSD is brand new (purchased from NewEgg a week ago based on rating/reviews/price/brand: a Kingston SSDnow300V) I'd still like to make whatever tweaks I can to reduce wear on it since I tend to keep the same hardware for a long time and would like the SSD to last as long as possible. 


Ext4/Journaling: I've been choosing Ext4 for most drives connected to the Ubuntu PC more out of habit than anything else... it's not an option I had experience with before I switched to Ubuntu but when given a choice I chose Ext4 since the 10.04 installer seemed to use it. I don't recall ever turning on/activating Journaling in Ubuntu (I recall avoiding it in MacOS) and I assume Journaling isn't on by default, but would like to verify that it's off.


Thanks again 1clue for the very clear and helpful overview of LVM, boot process, etc... 1clue! :-) It really helps!


Enough RAM to avoid swap: my old PC had 4GB of RAM and as far as I know/recall, it never went into swap. The new (early i7) PC has 8GB, so I can't imagine swap will be an issue. From back in my SGI days, I DO recall how heavy swap activity would cripple a process.


Assuming there are no major downsides to using 'noatime' and making sure Journaling is off, I'd like to do both simply to make life a bit easier on the SSD, even if it's new enough to not warrant such precautions. Just for peace of mind. :-) Perhaps I could impose upon you fellas for some guidance with that?


TO SUM UP: just to keep things simple/basic, considering that most of the advantages of LVM don't really apply to me, I'm inclined to go ahead and wipe the SSD and do a regular/standard reinstall of 13.04 without it. AFTER that's done, I'd very much appreciate a bit more guidance to take modest steps to 'protect' the SSD by using 'noatime' (assuming that doing so doesn't have negative implications I don't know about), verifying that Journaling is off, etc...  I'm going to do the reinstall in a couple hours and will come back then. 

**THANKS AGAIN for all the help.**

---

### Post by oldfred on 2013-11-08
You can leave /home inside / (root). I often suggest separate /mnt/data or /home to keep / smaller, but since SSD is not a new large multi-TB drive / size is not critical. The only other advantage of separate /home is you can reinstall and keep data, but you should be backing up /home anyway and if inside / you share the unused space so sizing of partitions is less critical.

These were the changes I did to my now 2 year old SSD. Some may have newer/better suggestions.
       With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.

I originally changed scheduler. But that now has changed.

 [http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)
noop may not be best scheduler for SSD, deadline may be better
[http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance](http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance)


 You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition
update/correction is that nodiratime is not required with noatime setting. 

   SSD Example mounting line:
UUID=41b6b187-be76-4447-b18b-d39cc744b184 /               ext4    noatime,discard,errors=remount-ro 0       1

I have seen this (and some other temporary folders), but have not done this:

 One other thing that saves writing small files to the SSD as long as you are not doing something that needs a lot of tmp space, since tmp is cleared on boot, is an fstab entry:But writing a DVD may need 4GB?
tmpfs        /tmp        tmpfs    nodev,nosuid    0    0

I also changed from using discard in fstab to a script and cron task.

 HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)
      
 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim

---

### Post by 1clue on 2013-11-08
The partition arrangement is one of preference and the needs of your situation.

You're just installing a workstation, so about all you'd really want to consider would be /home as was mentioned above.

Advantages of more partitions:
[LIST=1]
[*]If one partition is filled up you don't lose the others.  For example, if your /home partition fills up because you downloaded too much junk then your system can still function without SYSTEM errors.
[*]Some apps (databases, etc) have better performance if you use a certain type of partition, or use special tuning for that partition.
[*]Sometimes a security issue is simplified by using a partition.
[*]If you have one directory that writes a lot, (a database for example) then you can put it on a different partition so that a crash or power loss won't cause errors on the core system filesystem.
[*]Sometimes you want different directories on different drives.  One example:
[LIST=1]
[*]I have an ssd, a plain hdd and a raid array.
[*]My most expendable junk goes on the hdd.
[*]The stuff I want to be fast goes on the ssd.
[*]The stuff I want to be most protected from data damage goes on the raid array.
[*]I have LVM2 going, and each directory of a certain type gets a logical volume mounted there.
[*]LVM2 I can resize the partitions on the fly, so they don't use that much extra space.
[/LIST]
[/LIST]

Disadvantages:


[LIST=1]
[*]The more partitions/filesystems you use, the more attention you need to pay to keep your system going.
[*]If you have a lot of partitions, you will inevitably have a lot of space wasted by a non-full partition.
[*]The more complicated you get, the more you need to know/remember/manage about your system.
[/LIST]

---

### Post by bc9 on 2013-11-08
Thank you both. :-) I've re-installed 13.04 (w/o LVM) and moved all my drives/data over from the old PC to the new one. 

I'm in the process of trying to find/reorganize all my stuff, which is going slower than I'd have hoped, mainly due to me not being familiar with the Unity GUI. Also, I installed Chrome but it seems to hang the entire PC after a little while (have to unplug the box to restart) so I'm using Firefox instead now (Chrome's been my preferred/stable browser since it came out, but I can go back to Firefox if necessary). My impression of 13.04 w/Unity are the same as last time I briefly tasted it: it makes me miss 10.04 w/Gnome. I know I can install the Gnome2 Flashback thing, but I thought I'd try to get used to 13.04 as-is first... at least give it a real try. I don't even see how to put an often-used folder into the 'Places' section of a file window Sidebar... in 10.04 it was simply drag (the folder) and drop (it into the Sidebar) but that doesn't seem to be an option now. 

I'm also having some permissions issues... on the physical hard drive that *used* to be the system drive on the old PC. It seems there are going to be a LOT of little things like that for me to get used to/figure out.

I don't want to bother you with stuff like that... just give me a bit of time to get situated and I'll follow up re: noatime, etc... Thanks again!


*Added later: I guess I spoke too soon, it's not simply Chrome that's a problem... it's hanging the PC even when I'm using Firefox... so it's probably not related to either program. It's a complete freeze: the cursor doesn't respond to the mouse (so I can't do anything in the GUI like kill a process)... the power/reset buttons on the PC itself don't respond either. I have to unplug the whole machine, losing any work in progress. It's going to take me a while to figure this out. I suppose there are clues in a logfile somewhere but I've got no idea where it is or how to read it. Short term, I have to have a working PC... so I have t decide if I'm going to try to 'go back' to the old one or set up a temporary/third one or what.*

---

### Post by oldfred on 2013-11-08
I went from 10.10 to 12.04 and installed fallback, so I could have menus. Also my screen is 4:3 so top & bottom for panels work better for me.
 I am not sure there was a working fallback with 12.10 or 13.04? As it now needs Gnome 3.8.

Just today I installed flashback into my 14.04 install and it seems to be similar, but menu items have moved all over the place. Also with 14.04 getting regular errors, but it seems to keep working.

---

### Post by bc9 on 2013-11-09
As mentioned, the PC is having an issue and I haven't yet figured out the cause (I don't THINK it's due to Ubuntu) per the attached photo I took of the screen following one of the many freezes/crashes it had today.

Tomorrow I will re-seat all the RAM, check to see that the Nvidia drivers are the most current and if neither of those alleviate the problem, I guess I'll take out the SSD and try booting 13.04 from a regular hard drive instead to see if that makes a difference. If it's STILL happening after all of that, I'll put in a Windows 7 system/boot drive and see whether the freeze/hang happens with that... if so, it's gotta be hardware. I'm loathe to remove/reinstall the CPU, but I'll cross that bridge if and when I come to it.

It's always something. ;)

---

### Post by oldfred on 2013-11-09
What system, cpu etc.
Some need extra boot parameters to work well or work around various bugs.

 [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by mc4man on 2013-11-10
From all I've read & from my ssd maker don't see any reason to add discard, nor to worry about trim in newer ssd's, the drive will take care of itself.
Though to give a little 'helping' hand I do leave some unallocated space at end of drive, 10gb here.

---

### Post by bc9 on 2013-11-10
Well, I haven't managed to get the freezing/hanging problem resolved... I thought I did yesterday, but it's happening again today though I'm not positive it's the same problem as before. 

Yesterday I re-seated all the RAM and the video card. Then I updated the system software (Software and Updates from System Settings) ...it wanted 140MB of various updates. I'm not sure why it needed so much since I only just installed everything the day before and I thought that it's supposed to go online to get all the updates at that time. Finally, I changed from the installed open-source (default I suppose) display driver to the proprietary/tested one: [ATTACH=CONFIG]247732[/ATTACH]

...after all that the system ran fine (as far as I know/could tell) for 12 hours straight. That was yesterday... and today it's hanging again. Of the three times it froze today, I only happened to be in front of it to see it happen once. I had Chrome open and a file downloading and I was editing a file name in a folder window. Literally mid-edit the system stopped taking any input from the keyboard and mouse at all, though the GUI itself was still updating (I could see the download stats changing, so that process was still running and the lights on the router were still blinking). After X amount of time, the screen saver cut in so the display went black, though I assume the download was still going. I did try unplugging and replugging the USB keyboard and mouse, but that didn't help/wake it up to accept input. Eventually, I power-cycled the machine (by unplugging it from the wall) just as I had to to twice earlier today. 

Things I could try now: 

I could update from Ubuntu 13.04 to 13.10 to see if some bug got fixed in the update (I normally decline incremental version updates)
I could install 13.04 on a regular hard drive and see if the system runs any better than way (instead of running it from the install on the SSD)
I could boot the system from Windows (using a different hard drive) instead but I'm not really interested in running Windows at all. 

...other than that, I'm out of ideas at the moment. Obviously, I'd like to get the machine running/stable and THEN I can worry later about noatime or other tweaks.

System specs :

Intel DX58SO logic board with Intel Xeon CPU W3540 @ 2.93GHz (8 cores)
8GB RAM (shows as 7.8 in system details)
NVIDIA Geforce PNY GTX480 PCIe/SSE2 display card using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-310 (propietary, tested)
Ubuntu 13.04 (64 bit) updated yesterday, booting from Kingston 120GB SSD (purchased last week from Newegg)

If anyone's interested/able to suggest something to help, and requires more info (I'm happy to go find a logfile or whatever if told where/which one to examine) please do. TIA! :-)

---

### Post by oldfred on 2013-11-10
First do not power cycle except as a last resort. Better to remember the elephants. And it may work even if keyboard seems locked.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

If it hangs, switch to terminal and run top to see what is running and consumming resorces. Or look at system monitor if you can get to that.

---

### Post by bc9 on 2013-11-13
Thanks for the info oldfred... I've never heard of that before (REISUB) but will try it next time (the elephant acromyn is very good ;-)). When it happens, I can't get a terminal window or open anything... literally every keyboard and mouse input seems to be ignored, as if they were unplugged. But I'll try the REISUB next time despite my impression that the system isn't listening to the keyboard at all by that point.

I was busy w/work but am back at it... last night I began what seemed like the next-least-drastic step: upgrading from 13.04 to 13.10 but (of course) my system froze partway through the installation. After waiting forever (hoping it might come back and finish, or at least exit the install gracefully) it was clear that it was totally hung. After rebooting (I was relieved that it did) 13.04 still ran but I think the Software Updater no longer works... when I tried to use it again to proceed/finish the update, it just 'checked for updates' indefinitely. 

Maybe there is a problem with my particular SSD, or maybe there's some problem with Ubuntu on my particular bits of hardware... I don't know. Since the crash during upgrade last night seems to have crippled Software Updater, I figure I should probably start over since I don't have much confidence in the integrity of the install of 13.04 now on my machine. So, I'll wipe the SSD and start again... I'll also try the current Mint to see if there's any difference (I know it's from the same branch of the Linux family tree as Ubuntu, but (I'm told) it might be worth trying, just to see if my freeze/hang problem goes away or not). 

Then there's the option of starting over without the SSD. It's all a bit demoralizing... I don't really have the time to futz with this due to work, nor did I expect changing PCs and versions of Ubuntu would have eaten up as much of my time as it has over the past week.

I'll keep you updated. Thanks again SINCERELY for your help. :-)

***ADDED LATER: ***[I]the same freezing of the system happens under Mint. Also: as suspected, the alt+SysRq then REISUB doesn't work (I tried a few times, with and without caps, etc...). I put in a regular hard drive and am currently installing the OS (yet again) on it to remove the SSD from the equation. More to follow...

**ADDED STILL LATER:** thought that I'd solved the problem (again) when it ran for three hours today once I removed the SSD and put Mint on a regular hard drive. But of course, I was mistaken... it froze again a little while ago. I've tried two distributions of Linux, two different graphics adapters, three different quantities of RAM and running with the system on the original SSD as well as a regular hard drive. I also re-seated all the RAM and tried having the boot drive on different SATA ports. Eventually, it freezes/crashes with each of these attempts/configurations and I'm sort of out of ideas. [/I]

---

