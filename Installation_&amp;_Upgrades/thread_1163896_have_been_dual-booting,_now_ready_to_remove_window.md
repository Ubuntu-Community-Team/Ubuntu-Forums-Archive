---
title: "have been dual-booting, now ready to remove windows..."
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by clairefun on 2009-05-19
Hi all,
As the title says, I've been dual-booting ubuntu and windows for the last couple of weeks. It's been a learning curve - I'm a complete linux noob, and a little nervous of the terminal, as I don't know what I'm doing. I've been using PCs for almost 20 years so it's quite a strange feeling to just have no idea. I had to fiddle about with partition sizes and assorted bits of software that haven't quite been working right but am now - I think, I hope - ready to just get rid of the windows stuff and reclaim the space it takes up for ubuntu. What's the best way to do this? I don't want to have to reinstall from the live CD if I can help it (as I've made lots of fiddly little changes here and there) and I don't *believe* I have any personal files I care much about in my windows directory. Should I just delete assorted folders and use g-parted again, or is there a better way? And is there anything in my windows files that I should check? Most of my documents/mp3s/photographs etc are on a different drive anyway.

Thanking you in advance for your help and advice - the amount of reading of this place I've done recertly I know you're a friendly and helpful bunch before I even posted anything myself :)

Claire

---

### Post by dandnsmith on 2009-05-19
Do you consider it essential to recover the space used for Windows?
If the answer is either no, or you're not sure, then I'd counsel leaving things until you've a bit more experience.

The risks are mostly to do with rendering the PC unbootable - you haven't posted enough detail about the setup to allow for a proper assessment.
What you need to know (for a start) is
- what partitions you have on the HDD (hard disk)
- where GRUB is installed
- where the GRUB files are which it uses during booting
- how to recover the bootability if you mess things up.

---

### Post by coffeecat on 2009-05-19
I agree with dandnsmith - unless you're really short of space, leave Windows where it is. You can access your Windows partition from Ubuntu - have a look in the Places menu - because Ubuntu has had ntfs read and write support for quire some time now. Why not use your Windows C: partition as a storage partition? Just create a new folder for this and ignore the /Windows, /Program Files and /Users folders. Then if you do need to go back to Windows for whatever reason, even if temporarily, you haven't burnt your bridges.

If you do want to use your Windows partition for data storage and want this mounted automatically on bootup, post back and someone will help you edit /etc/fstab for this.

---

### Post by clairefun on 2009-05-19
Hmm, I see. I need to recover at least *some* of the space, as my ubuntu space is shrinking rapidly. I know (or can find out) what partitions I have, but no idea about the other things you listed. 

My partitions are : (and I'm probably giving you more stuff than you need to know, 'cause I don't know what's important and what isn't, my apologies if so):

/dev/sda1 (file system fat 16 label Dell Utility)
/dev/sda2 ntfs (used 27GB, unused 9GB,flagged boot)
/dev/sda4 extended (flagged lba)
    /dev/sda5 ext3 (used 18gb unused 6.62GB)
    /dev/sda6 linux-swap (size 1.65)
    unallocated 588 mib
unallocated 541mb
/dev/sda3 (file system fat32)

Not that I know anything much about what that all means, but the ext3 one is the ubuntu space, yes? 

I'm willing to give you the rest of the things you need, but don't know how to find them out, I'm afraid.

---

### Post by coffeecat on 2009-05-19
OK, first thing is that your Windows C: partition (sda2) is a primary. It has to be. Your Ubuntu root partition (sda5) is a logical. And they are not contiguous. Two reasons why you can't merge your Ubuntu root partition with sda2. Which means that unless you completely repartition your hard drive - which would mean a reinstall - you might as well use sda2 as a data partition. You have two options:

1 Use sda2 as is. Simply delete everything on it. You'll then have about 36 GB usable space. Use the Places menu, or edit your fstab as I suggested earlier and you have a usable partition. For neatness, you's also want to edit your grub menu so that you boot up automatically into Ubuntu - we can help you with that.

Option 2 - There's also a FAT32 partition (sda3). How big is it? **If** it is contiguous with sda2, you could make one bigger partition in the space of both. Open a terminal (Applications > Accessories) and post the ouput of:

```
sudo fdisk -l
```That'll give us the little bit more information we need.

Another thing to think about: NTFS and FAT32 are Microsoft filesystems. Nothing wrong with that, but if they need repairing, that's best done with the Windows chkdsk utility. If you have a Linux-only system, you might be better off with a Linux filesystem such as ext3 in place of sda2 +- sda3. When you've posted fdisk, we'll have a better idea.

**Edit:** one other question. Is sda1, the Dell utility, a restore partition or do you have separate restore CDs?

---

### Post by fletchoid on 2009-05-19
> **clairefun said:**
> .... My partitions are : (and I'm probably giving you more stuff than you need to know, 'cause I don't know what's important and what isn't, my apologies if so):

/**dev/sda1 (file system fat 16 label Dell Utility)**
/dev/sda2 ntfs (used 27GB, unused 9GB,flagged boot)
/dev/sda4 extended (flagged lba)
    /dev/sda5 ext3 (used 18gb unused 6.62GB)
    /dev/sda6 linux-swap (size 1.65)
    unallocated 588 mib
unallocated 541mb
/dev/sda3 (file system fat32)

Be very careful.  I know of several incidences where  messing with the Dell Utility partition buggered the whole drive.  You are probably not sure exactly where your GRUB file is located, and you might lose it, and not be able to boot at all.
My suggestion would be to do the following:
1.  Using Windows Add Remove programs, remove any programs you will NEVER use, to make space on the drive.  Leave the Windows OS files alone.
2.  In the Windows partition, delete any useless data (old movies, mp3, etc.)
3.  Defrag the Windows partition at least twice.  Sometimes one pass leave a few files fragmented.
4.  As in the advice from previous posts, use the ntfs partition to store data (like music, movies, etc.)  
Unless you really know what you are doing, deleting the Windows partition, and the Dell partition, could leave you with a broken GRUB file, and unable to boot into anything.  This situation is recoverable, but you need to know what you are doing, or you could waste a lot of time getting things to work again.  If you really want to use Ubuntu exclusively, I would recommend buying a new hard drive (bigger if you like) and doing a fresh install of Ubuntu.  Keep the old hard drive around in case you ever need to go back to it.  When you feel you are a total pro, you could always use the old drive for more storage space.  Of course this is assuming you aren't using a laptop with only one drive.

---

### Post by montini on 2009-05-19
> **clairefun said:**
> 

/dev/sda1 (file system fat 16 label Dell Utility)
/dev/sda2 ntfs (used 27GB, unused 9GB,flagged boot)
/dev/sda4 extended (flagged lba)
    /dev/sda5 ext3 (used 18gb unused 6.62GB)
    /dev/sda6 linux-swap (size 1.65)
    unallocated 588 mib
unallocated 541mb
/dev/sda3 (file system fat32)



Judging from this, I would propose clean install with erasing every partition except maybe "Dell Utility" (maybe this is system preinstall partition?), and then making new partitions as follows:

~15-20GB for root mount point ("/") - ext3 (or ext4), labeling as boot
~(all that left minus ~900MB) for home partition ("/home") - ext3
~900MB for linux swap space

of course, in this case you should first backup your data somewhere, but believe me, getting separate "/home" partition is very handful for the future.

---

### Post by glotz on 2009-05-19
When I removed my winders partition years ago I made two lists of the stuff that's important to me to not lose any. Top down and bottom up, that is I listed all the programs I had which were useful to me and then did a painstaking inventory of all the files on my windoze disk. I don't have those lists any more and can't remember what I found but I do remember it was a rather good idea, there's a surprising amount of stuff around...

You don't have to delete anything, just fire up gparted and zap the partition and make a new one or resize existing partitions. You might want to download the [latest gparted liveCD version](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779) for the job.

You might also want to make sure you've cleared your package cache in Ubuntu to save space, in system > admin > synaptic > settings > prefs > files > delete cached packages.

Welcome to freedom Claire!

---

### Post by clairefun on 2009-05-19
wow - thank you everyone!

SO my options are a complete reinstall / re-partitioning, or using as-is, basically. Here's the f-disk results : 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *         289        5143    38997787+   7  HPFS/NTFS
/dev/sda3            9436        9726     2337457+  db  CP/M / CTOS / ...
/dev/sda4            5753        9366    29029455    f  W95 Ext'd (LBA)
/dev/sda5            5753        9075    26691966   83  Linux
/dev/sda6            9076        9291     1734988+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01509951

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601    7  HPFS/NTFS

Hope that helps..?

I *do* have restore discs, but seeing as how they're Dell, they don't aactually contain half the things I need, like drivers, and software, and any sort of compatibility with usb at ALL. I've done one restore-from-restore-disks on it and vowed to never bother again ;) 

Space for storage of music & media isn't an issue as I have a separate drive full of random stuff, though I've had to move my (large) collection of wallpapers to the linux drive for the pictures folder screensaver to work, fter a few days of 'playing' (swearing at) f-spot. I guess that's why I'm starting to worry about the only-6gb-left on linux partition. I have *no* idea how many more programs or whatever I'm going to want to install into my linux space, and 6 gb doesn't seem like it gives me that much leeway.  Or is it loads really and I'm worrying unnecessarily anyway?

I don't feel at the moment the urge to ever use windows again, and have only stuck with it so long because I knew what I was doing even when it went wrong, and 'here' I know nothing! software wise I've got everythig I use / need, or I can find a pretty good replacement for, and I'm not a big gamer - I have a console for that. (I know that some games I used to play are windows games, but hey, my pcs getting to the stage where it won't play brand new releases anyway). Last time I tried, picasa didn't work that well, but it seems to be fine now, and I've got a pretty dock (cairo-dock) set up too so everything looks quite nice. Nicer than windows ever did, to be honest. I preferred the Gimp to photoshop already...nah, no more windows for me! :)

---

### Post by coffeecat on 2009-05-19
Now I've seen you fdisk, I'd say that if you're determined to be rid of Windows, then do a fresh install and let the installer use the whole disk. Your partition layout is a mess at the moment - pardon me, that's not a criticism. It's just inevitable when you're trying to work round Dell's way of setting up the drive. A fresh install will give you a neat and efficient layout.

However, don't take my word for it. Wait for others to post! :)

> **clairefun said:**
> 
I *do* have restore discs, but seeing as how they're Dell, they don't aactually contain half the things I need, like drivers, and software, and any sort of compatibility with usb at ALL

That's absolutely extraordinary. A manufacturer provides restore discs that don't have the drivers for the hardware! I think this deserves **three** emoticons: :shock: :roll: ](*,)

---

### Post by montini on 2009-05-19
> **clairefun said:**
> ... and I've got a pretty dock (cairo-dock) set up too so everything looks quite nice. 

hey, look at another option - "gnome-do" with "docky". I've found it just a few days ago, but I already dumped my avant window navigator (avn) dock for the docky :) it's really nice and fast - not to mention the main innovative functionality presented by gnome-do ([http://do.davebsd.com/](http://do.davebsd.com/)). You will find it on synaptic!

---

### Post by clairefun on 2009-05-19
> **coffeecat said:**
> Now I've seen you fdisk, I'd say that if you're determined to be rid of Windows, then do a fresh install and let the installer use the whole disk. Your partition layout is a mess at the moment - pardon me, that's not a criticism. It's just inevitable when you're trying to work round Dell's way of setting up the drive. A fresh install will give you a neat and efficient layout. 

No offense taken, it certainly took some smoodging about in g-parted to get enough space for linux to run, so I was aware that I'd made a bit of a mess in there. (Smoodging is the technical term for what I did, yes).

[quote}That's absolutely extraordinary. A manufacturer provides restore discs that don't have the drivers for the hardware! I think this deserves **three** emoticons: :shock: :roll: ](*,)[/quote]

Yes, I found it quite, uh, 'impressive' at the time. It's well-known to have pleased a LOT of people too! ;) It does drive me a bit crazy, especially as it's supposed to be easy for non-computer-savvy people to be able to use. My mum and sister have been looking at dells and I hate to think what they'd do if they got to that point. (Well, they'd call me, but that's not what I mean!). At least with moving to ubuntu it's long had history of not being that user-friendly to people with no tech knowledge - I've been pleasantly surprised by how easy some of the things I've had to work out have been. Not that I'd recommend it to my mum just yet, but it's nice to think one day...of course, my mum has only just found out how to buy something from amazon and even then it takes about half an hour, so maybe ubuntu is not for her :D 

SO one vote for fresh install onto whole disk. That feels a very exciting step!

---

### Post by clairefun on 2009-05-19
> **montini said:**
> hey, look at another option - "gnome-do" with "docky". I've found it just a few days ago, but I already dumped my avant window navigator (avn) dock for the docky :) it's really nice and fast - not to mention the main innovative functionality presented by gnome-do ([http://do.davebsd.com/](http://do.davebsd.com/)). You will find it on synaptic!

Thanks for that, maybe if I do a reinstall I'll look at that instead of CairoDock (although I am quite happy with it, though my compiz doesn't work perfectly). I did have a quick look when I was looking into docks - but I didn't really understand what gnome-do is and thought that just knowing what I have with just the gnome stuff might be simpler for me. I didn't want to risk that it might make things less easy for me to understand! (I am an ubuntu coward at the moment...)

---

### Post by glotz on 2009-05-19
One more thing to consider is the versions. Do you know about the LTS versions? A reinstall would allow you to choose a LTS version if preferred. A LTS won't have the latest shinies but you won't have to upgrade so soon, if you don't feel like it.

A normal version is supported 18 months and a LTS version for 36 months. (on desktop)

Here's the release & support schedule. ([source](http://www.markshuttleworth.com/archives/146))
[[img]http://img245.imageshack.us/img245/1228/ubuntureleasecycle.png[/img]](http://www.markshuttleworth.com/archives/146)

---

### Post by clairefun on 2009-05-19
That's long term support, yes? I do read a lot of problems with people upgrading from one to another, but what difference does it make? I mean, once the next lts release comes out, does that mean that nobody will release things that work on this release? Never having used a release before this one, I rally don't know if that's something I need to worry about. I wouldn't at the moment really want to go to a different release - if they are that different - as I feel that I'm just starting to learn this whole thing. 18 months is a pretty good support time, and hopefully by then I should know what I'm doing well enough to cope with the change ;)

---

### Post by coffeecat on 2009-05-19
> **clairefun said:**
> 18 months is a pretty good support time

I do fresh installs every six months with the new releases. I guess it's a lot quicker than restoring Windows from a Dell restore CD. :lol:

Just one thing to add if you're going to do a fresh install. Sometimes manufacturers do peculiar things to the partition table. And I wouldn't put it past Dell to do something really peculiar. If the installer crashes or hangs when you get to the partitioning stage, bail out, go to Gparted (in the live CD) and then Device > Create Partition Table and create a new MSDOS partition table. It's satisfying to see Windows and its partitions disappear into that great bit dump in the sky. Then the installer should be fine.

---

### Post by montini on 2009-05-19
> **clairefun said:**
> Thanks for that, maybe if I do a reinstall I'll look at that instead of CairoDock (although I am quite happy with it, though my compiz doesn't work perfectly). I did have a quick look when I was looking into docks - but I didn't really understand what gnome-do is and thought that just knowing what I have with just the gnome stuff might be simpler for me. I didn't want to risk that it might make things less easy for me to understand! (I am an ubuntu coward at the moment...)

when I was making a decision - cairo-dock or awn - awn won because cairo was too slow for my taste. Docky animations are faster than cairo (I would say the same speed or higher as awn) and you still get that mouse_over-zoom_in effect like in osx.

---

### Post by montini on 2009-05-19
> **coffeecat said:**
> I do fresh installs every six months with the new releases. I guess it's a lot quicker than restoring Windows from a Dell restore CD. :lol:


And that's where separate "/home" partition comes in handy.

---

### Post by fabounet on 2009-05-19
> cairo was too slow for my taste
you didn't try Cairo-Dock2 ;-)

---

### Post by clairefun on 2009-05-20
Just wanted to update and say thanks to everyone who posted here for me - I now have a lovely 65gb-free ubuntu drive with nothing else on it - windows is nowhere to be seen! My re-installation has gone fine, I'm connected to my wireless network, I've reinstalled a few million packages and I *think* they all work fine, I'm playing about with my dock again, and all is well with the world - so big big thanks to everyone. Especially coffeecat, I think I love you. I feel ridiculously excited to have gotten rid of windows! (and extremely pleased with myself that I've managed to do it with just a little bit of advice here and there, too!).

I shall raise a glass to each of you in turn this evening :D

---

### Post by coffeecat on 2009-05-20
:oops: :oops: :oops:

:wink:

Congratulations and happy Ubuntu-ing! :)

---

