---
title: "Getting P.O.'d with Grub! (error 17, wierd setup here) Sil0680"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by Aacron on 2009-06-22
Okay,
 I've posted about this before in another thread but in a different context, here: [http://ubuntuforums.org/showthread.php?t=981138](http://ubuntuforums.org/showthread.php?t=981138)

 I've tried everything I know how to try, and I'm getting frustrated and this is exactly what has kept me from using Ubuntu (its the only one I like the UI and ease of working with since I'm Win-tarded).

  I have a Sil0680 add-in card, because my motherboard only has one IDE port.  Since I don't have a floppy drive at all, and I haven't ironed out how I want to slipstream the 680's drivers onto the install CD, the HD windows lives on is on the motherboard's IDE channel.

  Once *in* windows and the drivers are installed, windows has no issue whatsoever seeing the stuff on the 680, whether it is just drive 1-4, or in raid.  No problems what-so-ever.

  Ubuntu on the other hand, doesn't see stuff on the 680 correctly, and when I install it, somehow its putting the wrong information there for GRUB.  I think I have a little insight, but not much.

Here is my hard-drive layout:

Onboard IDE:
plextor DVD-RW (master)
Seagate 80GB (slave) [windows xp pro]

Sil 0680:
WD400 40GB (primary master, 1st drive in raid stripe)
Maxtor 40GB (primary slave, not in raid) [Ubuntu]
WD400 40GB (secondary master, 2nd drive in raid stripe)
nothing (sec slave)

In BIOS (MSI K9N Neo-F v1 nVidia 550MCP, award BIOS), the boot order is:
CDROM
ST[bunch of numbers] (seagate)
disabled
disabled

in hard drive list: (** is numbers for serial number or model)
IDE: ST8****
RAID1: Maxtor ****
RAID0: Sil0680 Set1 (something like that)
```
===========begin ranting===========
```
Now, I'm not a complete idiot, and can dance around most issues (at least in windows/dos).  I know my hardware stuff, and all that jazz.  So I'm failing to see what exactly is going on, other than an inkling of an idea I just had while using the SGD to boot back to windows since grub is barfing all over the place again.

Seems to me that since Ubuntu isn't getting the RAID right at all, maybe it is telling grub the wrong information.  Ubuntu sees: sda (onboard IDE but its NOT SATA so *should* be hda!), sdb (sil0680 PM), sdc (PS, ubuntu lives here), sdd (SM, second drive in set).

Now since even clunky retarded **windows** can figure out the raid, boots fine, yada yada, i would think that *nix would be spot-on and better than windows!!  WinXP actually gets the stuff backwards and still works... it sees the RAID as (0,0) the ubuntu disk as (0,1) and windows which is on the mobo IDE chanell is seen as (1,0).  So linux does have at least that right.
```
===========end ranting===========
```
Anyhow... on to the insight I have thought of:
Could GRUB be seeing things **properly** since it is running before the 'higher level' OS's go and screw up its day?  I get error 17... means it cant find the partition, if I get this right.  is there a way to boot to grub, not have it load s**t but just sit there, with some kind of way to enter commands/etc, so I can see what grub sees before the wonderful OS up and ruins the day?  I *think* that what grub is seeing, and what Ubuntu *thinks* grub should load are completely different since GRUB might actually be seeing the RAID set as one drive since that is what BIOS sees it as.

I've tried EVERYTHING that I know of, and I'm getting fed the [bleep] up here.  Super grub disk hard-locks my system when it gets to "embed *something something* stage5", so that isn't an option to fix things...  I abosultely freaking refuse to use the NTLDR>grub4dos>grub>ubuntu junk cause I dont want to have to baby-sit the freaking computer every time it boots, while it asks me through 2 different boot-loaders what to boot....

Please for the love of the god(s), please please please help me out here!!
I want to be able to use Ubuntu the way it is supposed to be used instead of this hectic mess I have now, so I have learn linux properly and not *have* to have windowsXX to get by!

---

### Post by Aacron on 2009-06-22
Anyone?  (really should have chosen a better subject but ARGH!!!)

---

### Post by dstew on 2009-06-22
> Ubuntu on the other hand, doesn't see stuff on the 680 correctly, and when I install it, somehow its putting the wrong information there for GRUB.I assume you get the grub error 17 before you see any grub menu, and that you get just the error number without a verbal explanation. Is that correct? If so, it means grub's stage1.5 was directed at installation to a partition that does not have a recognizable file system. This will happen if you have a RAID that is not recognized by the installer program on the Live CD. To install grub onto a RAID, you have to install the dmraid program onto the Live CD system. See the [FakeRAID How-To]("https://help.ubuntu.com/community/FakeRaidHowto"). I believe this holds even if you are not installing Ubuntu to a RAIDed partition. If you don't have dmraid going, the installer will not count the file systems correctly, and grub will be looking for its menu in one of the RAID partitions.

It is also possible that there is no Linux support for that hardware. I looked around, and could see only trouble in Linux-land from that card. It will work in Windows, because the card manufacturer and Microsoft have worked together to create good drivers. Often, manufacturers ignore Linux, or make only a gesture of support that produces a "driver" doesn't work well. So, even if you install dmraid, it is possible the Live CD will not be able to work with that hardware, and will only see the disks as ordinary individual disks.

---

### Post by Aacron on 2009-06-22
that guide seems neat... but i do remember an *old* SUSE install detecting and working fine a couple years back... 
When i enter the commands for the page you posted, I get this:
```

ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "sil_ajagddadagai" was activated
ERROR: dos: partition address past end of RAID device

```Thing is, I *can* get into ubuntu with this card, I just have to use the super grub cd, and manually boot in.

I think maybe... just maybe, if I change the order of the drives to where windows lives on the SIIG card and linux is happily living on the on-board IDE, I might just be able to get it to work.

But then I somehow have to tell ubuntu how to properly read the raid1 stripe set once I'm booted in so that it plays nice with it.  Generally use it for games/backups.  It'd just be nice to be able to do this out of the box....

ubuntu sees the drives... maybe it just doesn't support the card when RAID is used?

maybe I have the wrong firmware on the card too... using the raid firmware.. there is a simple IDE firmware as well, but then no raid :|

---

### Post by dstew on 2009-06-22
If the Supergrub disk can boot Ubuntu, you might be able [re-install grub]("http://ubuntuforums.org/showthread.php?t=224351") in a way that would work. Probably, it is a matter of getting the correct grub root. You could just try several different roots when trying to re-install grub. The grub root command causes the stage1 file to be installed into the MBR with a particular block address for the partition that contains stage2.

However, since the supergrub disk runs a linux kernel, it might be able to see things that native grub cannot. So it is not a sure thing.

If you want to get really grub-by, you can make a [native grub boot disk]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy"). That way, you will be installing grub in a native grub environment. You can use the tab-complete feature of the grub commands to look at the root directories of different partitions, and figure out which partition contains the grub stage2 and menu.lst files. If you do it with grub natively, there is no chance for error in the partition designation.

Once you get Ubuntu to boot, you might be able to see the RAID with dmraid. I am not sure what the error means, maybe on a hard-disk installed system it will work better, I don't know. And, as you say, maybe the hardware would not be recognized.

---

### Post by Aacron on 2009-06-22
Well, I just finished (finally) re-installing Windows XP Pro 32-bit... sitting here with the case cracked open and ribbons all over. :(

Installing Windows on the main IDE, just installed the SiiG drivers, and now about to move it to the SiiG controller... Hopefully this works.  Least if it doesn't, I'm hoping since Ubuntu is goign to be on the IDE and as the first bootable drive (at least in BIOS) then it won't go overwriting the MBR on the windows partition, and just use it's own drive for that (since it would be seen by BIOS first anyway, so the M$ one would be just chilling out)

Is dmraid installed by default?  Guessing it is loaded as a plugin module, and not compiled right into the kernel?  Dunno which is better/more compatible/etc.  Not 100% on my linux boot procedures :P  This whole grub thing is kidna wanky to me actually. :confused:


Will repost when I have Ubuntu installed again and (hopefully) grub will let me load straight in... *prays to the hardware/grub gods*

---

### Post by Aacron on 2009-06-22
============UPDATE:

Well, got Ubuntu installed now, and Grub WORKS!! well... at last it loads and boots linux.... :P

I can't get to the windows disk now :|

since grubby little grub is now working, (happy) is there something I can do from within the grub bootloader to see if I can figure out what to edit my grub.conf with to point it at the *correct* disk?

I keep looking around on google but the stuff I'm finding isn't really helping me out much... either it looks right but it throws my brain for a loop, or it doesn't seem to relate to what I'm actually looking at here.

EDIT TO DRIVE ORDERS: the maxtor that Ubuntu is installed to is now on primary slave IDE, and the windows drive is now on the SIL0680 Primary slave ribbon.

[COLOR=Blue]Basically what I think I need to find is a command within grub (I have a native cd ready) to determine what drives it sees... /me doesn't know where I saw it before... sigh[/COLOR]

---

### Post by Aacron on 2009-06-23
YAY! Figured it out!
Ubuntu *is* messing up when you use an IDE card similar to mine, and you have a stripe set configured via the IDE-card's built-in bios!

Ubuntu's original menu.lst:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title                Microsoft Windows XP Professional
rootnoverify        (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1

```Modified to this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title                Microsoft Windows XP Professional
rootnoverify        (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```And now, XP Boots!!  yay!

So if any of the Ubuntu devs read this, perhaps the live-cd could include a method to detect not-quite-so-supported IDE-PATA/SATA RAID cards, and perhaps do something (looking at dmraid now to see if it works)... then no-one else will be sitting here for a year without Ubuntu, and then 4 straight days when they get fed up with M$ windows!

Technically, Ubuntu is configuring it right for what it *sees*, but grub apparently only sees what BIOS tells it to.  So my particular set-up had a quirk I noticed as I was dealing with this issue and testing out different things (and the many reformats from borking the drive info).  Has to do with the way BIOS reports drives, and the way Ubuntu is seeing them:

```

Physical        BIOS               GRUB             Ubuntu
--------------------------------------------------------------------------
IDE:P,M         CDROM              ??               cdrom
IDE:P,S         IDE:HDD            hd(0,0)          sda
Sil:P,S         RAID:HDD           hd(1,0)          sdc
Sil:P,M/S,M     RAID stripe1       ?hd(2,0)?        sdb
SiL:S,M         n/a                ??               sdd

```GRUB value for the raid-1 drive set I dunno how to get.  Imagine it's hd2, but I dunno the GRUB cli equivalent to 'fdisk -l', and couldn't find it after 3 days of google'ing.

Unfortunately I destroyed my raid stripe set while blindly trying to figure this out, so lost all my backed up data :(  If I can figure out how to get Ubuntu to 'correctly' get the stripe set detected and working I may post more here.  May help those who don't want to fumble around and ruin the data on a backup drive, or otherwise corrupt data on a raid array.

---

### Post by dstew on 2009-06-23
> Ubuntu is configuring it right for what it *sees*, but grub apparently only sees what BIOS tells it to.You have seen correctly. This insight is important for figuring out the most perplexing grub problems.> I dunno the GRUB cli equivalent to 'fdisk -l'There isn't one, but you can figure out the information using the grub **geometry** command (which will help you figure out which disk is which), and then using the **kernel** command followed by the tab-complete feature you can get partial directory listings of the root directories of the various partitions:```
grub>kernel (hd1,1)/<press the tab key>
```. If you really want to know what native grub is seeing, you need to use a grub boot floppy, because the grub *shell*, running on the live CD, is using the Linux disk enumeration, and the **map** function to translate Linux to grub, instead of using the BIOS enumeration, which is what native grub uses.

---

