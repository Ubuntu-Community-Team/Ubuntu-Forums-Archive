---
title: "HOWTO: Format a Western Digital USB hard drive as ext3, with automount"
date: 2009-07-22
forum: Hardware
---

### Post by todb on 2009-07-22
I was running low on disk space on my Ubuntu laptop, so I purchased a 1TB Western Digital "My Book" external USB 2.0 hard drive (for the Googlers, it's part # WDH1U10000 ). It comes with a bunch of auto-run cruft for Windows and Mac, so of course, that won't do. After a couple hours, I think I've settled on an easy step-by-step procedure to a) format the drive as ext3 (like my internal drive) and auto-mount the drive with normal read/write permissions for my usual user (in my case, "todb").

It's really not all that hard; I was initially over-complicating things by trying to fine-tune mount options in /etc/fstab, editing options with gconf-editor, wondering how hal works... but it turned out, in the end, to be fantastically simple.

This is all done on Ubuntu 8.10, "Intrepid Ibex."

** The Short Version **

[LIST=1]
[*]Plug in the drive
[*]Unmount the drive.
[*]Delete the existing partition and recreate it as ext3 with gparted
[*]Unplug the drive.
[*]Replug the drive.
[*]chown -R user:user /media/labelname
[/LIST]

Now for the longer-winded explanation:

**Plug It In**

Plug in the Western Digital Drive. You might be tempted to forgo the AC power supply, thinking that USB 2.0 will handle the power requirements. You will be wrong, and sorely disappointed when you get file system corruption.

** Unmount **

Once your drive is connected, the first order of business is to unmount it, since it's probably already mounted thanks to the automount USB magic. Right click on the icon on your desktop, and select "Unmount." If that doesn't work, try a command line unmount:

```
$ sudo umount /media/My\ Book
``` (or whatever it's called, it does ship with a space in the label name, which is irritating)

** Repartition **

Next, you'll want to nuke the factory-shipped configuration. The easiest way to do this is to get yourself GParted, if you don't have it already. From a terminal:

```
$ sudo apt-get install gparted
```

Then navigate to **System > Administration > Partition Editor**
If you have just the one internal drive, then your new drive will likely be recognized as the device **/dev/sdb**. There's a selection menu on the top right side of the screen, so select /dev/sdb.

You'll now be presented with the graphical display of the existing partition. Select it, then hit the big Delete button. Select the new unallocated gray space, and hit the New button. Choose **ext3** as the new filesystem, and choose a label without a space in the name (I went with the creative "MyBook"). Finally, to make all this happen, hit Apply. (If you screwed something up, hit Undo, and start over.

The reformatting will take a few minutes. Check your twitter feeds or something.

** Remount **

When it's done, close Gparted, yank the USB cable, wait around a few seconds, and plug it back in. Your drive should mount itself in /media/MyBook (or /media/WhateverYouLabelledItAs). If it doesn't, yank and replug again -- I've had the initial detection fail once in while, but this seems to be no big deal.

** Chown **

Sadly, your new ext3 drive, by default, will mount as root-owned. You can read and execute off it, but not write. I'll be pickled if I can't find out how to change the default mount options (I suspect it has to do with the arcane art of **gconf-editor**), but mine mounts as:

```

$ cat /etc/mtab
/dev/sdb1 /media/MyBook ext3 rw,nosuid,nodev,uhelper=hal 0 0


```

The easiest way to ensure that you can write to it is with chown. Assuming your user name is "todb" and your ext3 label is "MyBook", the terminal command is:

```

$ sudo chown -R todb:todb /media/MyBook

```

And that's it! If you know how to get fancier with the mount options, please feel free to reply to this telling us; my gconf-editor skills seem to be for naught. I think it just involves creating a new key under /system/storage/default_options for ext3 partitions, but what do I know. At any rate, this chowning method seems to work, and is persistent across mounts and reboots, so I'm happy with it for now.

Oh, and if you do intend to unplug the drive while it's running, it's probably best to first unmount it, to avoid wanging up any disk writes you might have going on:

```

$ umount /media/MyBook

```

Note that now that you own the drive, you no longer need to sudo umount.

HTH.

---

### Post by warfacegod on 2009-07-24
Thanks for posting this. I've had a hell of a time with this issue.
A few questions if you don't mind.

01. Does this work the same way with ext4 in 9.04?

02. Does it work for usb flash drives?

03. With two computers (both 9.04) with the same username on each, will each computer consider that user to be the owner?

Thanks much.

---

### Post by warfacegod on 2009-07-24
I would imagine this would be true for any brand hard drive, not only WD.
Just a thought.

---

### Post by todb on 2009-07-24
> **warfacegod said:**
> 
01. Does this work the same way with ext4 in 9.04?

Not having tried it, I would assume so. Of course, there may be different defaults in 9.04 that obviate the need for the ownership change.

> **warfacegod said:**
> 
02. Does it work for usb flash drives?

I see no reason why not, but you are encouraged to try and report back. :)

> **warfacegod said:**
> 
03. With two computers (both 9.04) with the same username on each, will each computer consider that user to be the owner?

Sadly, I don't know how ext3 (or ext4) stores the user identifier, though I expect it's by UID, not username -- so if you had the same UID on both computers, it should work -- since root is always UID 0, this is why root permissions will appear to persist across machines; this is also why I'd like something like mounting with an effective group permission.

Just to be clear: Chowning the drive, as I do, is almost certainly the Wrong Way to go about this, but I've failed to find the Right Way that's compatible with Ubuntu's (apparently magical) USB device mounting procedure. It does work for my purposes, and it's easy to implement.

---

### Post by nubbe on 2009-07-24
I have formatted a usb-drive with ext4 with no apparent problem. It even seemed that I got faster write-speed (note seemed...). 
No failure, catastrophic or otherwise yet.

---

### Post by nubbe on 2009-07-24
I use the chown way to get read/wrtite also on both ext3 and 4. 
I seem to remeber that it's UID# not username. So as long as u only use the drive locally or on machines where u got the same UID#, no prob.
When I want to move stuff, it's all FAT...

---

### Post by mister_playboy on 2009-07-24
Formatting a USB flash drive with ext3, ext4, or any other journalling FS is a bad idea.  The constant writes to the journal will degrade the life of the media significantly.  The only thing that would do in a USB flash drive more quickly would be to use it as RAM.

Thanks for the tutorial!  I'm will be migrating all my external drives to ext4... when I get another drive big enough to hold all the data!  :)

---

### Post by warfacegod on 2009-07-25
I have no idea if the defaults from 8.10 to 9.04 are different or not but with either one, when formating to any filesystem, I lost write privileges
on flash and hard drives.

I don't remember how I fixed that but eventually did after much foolishness and idiocy. I seem to remember lots of long winded terminal crap. This way worked instantly for my flash drive (PNY so yeah it isn't just WD). Why not simply have ubuntu ask for authentication like it for allot of other system type GUI commands?

---

### Post by warfacegod on 2009-07-25
Why would ext3 or 4 need more read/write operations than say FAT32 or NTFS hence shortening the flash drives life?

(Maybe their really out to kill my flash drive)

By the same logic, ext3 and 4 aught to do the same thing to a hard drive.

---

### Post by nubbe on 2009-07-25
if u use
sudo gparted
then it will be partitioned and formatted by root (and of course owned), that might explain ur rw probs.

---

### Post by watchpocket on 2010-07-19
> **todb said:**
> You'll now be presented with the graphical display of the existing partition. Select it, then hit the big Delete button. Select the new unallocated gray space, and hit the New button. Choose **ext3** as the new filesystem, 

I'm trying to format (for Karmic) a Western Digital 320GB "My Passport Studio" external drive, model WDMT3200TN.   It handles FireWire 800 & 400, and USB 2.0.

GParted presents me with ***three*** (pre-formatted) partitions on this disk. 

For the ***first*** small (31.50 KiB) partition ( /dev/sdb1 -- whose file system is "unknown" ) I get it that I can delete this one, in fact, "Delete" is the only choice I have that's not grayed-out for this partition.

I then have the gray unallocated ***second*** partition (128.00MiB), for which "New" is the only choice that's not grayed-out.  (Also, this is the only one of the three partitions for which "New"*[COLOR=Black] [COLOR=Black]**IS**[/COLOR][/COLOR]* an available choice).

For the ***third***, much larger, partition (297.97 GiB), ( /dev/sdb3,  formatted for the MacOS hfs+ file system ), the choices GParted offers are "Delete," "Resize/Move" and "Copy."

Should I simply delete the large hfs+ partition as well as the first small "unknown" one?  (I definitely don't want hfs+.)  Is it okay to have just one large partition, made from the unallocated partition?  (I'm only using this drive on Ubuntu -- for backups and maybe  photo or music collections.   I won't be using it with windows or mac or other OSes.)

Also, when I create the new partition using the "New" button, should I create it as "Primary Partition" or as "Extended Partition"  ?

And in what situation would I want to use "Linux-swap" as the file system?  Should I create a smaller partition for some swap or free space? (  If so, maybe that's the partition that should use a "Linux-swap" fs.)

And finally, why ext3 instead of ext4?   I may go with ext4 unless  someone has a reason not to.

I am (quite obviously) new to partitioning and formatting on Ubuntu.  ***[COLOR=Black]Thanks[/COLOR]*** for any tips.

---

### Post by todb on 2010-07-19
> **watchpocket said:**
> 

Should I simply delete the large hfs+ partition as well as the first small "unknown" one?  (I definitely don't want hfs+.)  Is it okay to have just one large partition, made from the unallocated partition?  (I'm only using this drive on Ubuntu -- for backups and maybe  photo or music collections.   I won't be using it with windows or mac or other OSes.)


I would. There are some reasons to have multiple partitions, but unless you are supernaturally organized with your data (or have different permissions needs) I wouldn't bother.

> Also, when I create the new partition using the "New" button, should I create it as "Primary Partition" or as "Extended Partition"  ?

Does GParted make this distinction obvious? (I don't recall). Since you're only going with one partition, it doesn't much matter. Go with Primary.

> And in what situation would I want to use "Linux-swap" as the file system?  Should I create a smaller partition for some swap or free space?

On a portable drive like this, never -- if you designate a swap partition, you will have lots more writes at unknown times, and if you're like me and always yanking the cable out without being a good computing citizen and umounting, you will certainly screw up the disk. If you're more familiar with Microsoft architecture, a swap partition to linux is what a paging file is to Windows.

> And finally, why ext3 instead of ext4?   I may go with ext4 unless  someone has a reason not to.

No particular reason. Other people on this thread are happy with their ext4's.

---

### Post by watchpocket on 2010-07-19
I decided to go with the ext3 file system since it's also what my Ubuntu box's internal HD uses.

However I ran into two problems: 

When I tried to delete the first small partition, I got this when I hit "Apply" : 

"*libparted messages: Partition map has no partition map entry!*" and it wouldn't delete.

And when I hit "New" to create a new empty partition from the unallocated one, I got this: "*libparted messages: Can't have overlapping partitions.*"

I ***was*** able to delete the third large hfs+ partition with no problem.

Not sure what to do, but somehow the "unknown" partition has to become "known" and able to be read.  Any and all suggestions welcome.

[Edit] Googling around on the error messages, looks like I should just try to  write the partition table and/or try to change that first block to ext3  or whatever.  I'll try this later when I'm home.

---

### Post by chris.olive on 2010-08-03
That looked really simple, and I would try it with my Compaq laptop and blue ring W/D drive, but for one problem.
Unbuntu will not recognize the drive, I can access it via "window shares" but when I plug it into USB port nothing shows, am I doing something wrong?
Lucid on this machine and a new desktop, but no joy on either, GParted does not locate it either.
Any ideas please.

---

### Post by yasmar on 2010-08-05
Thanks for the helpful instructions.

Instead of changing ownership of the drive (step 6), you could just open up the permissions:
sudo chmod a+w /media/labelname

I think this would be a more standard solution.

---

### Post by chris.olive on 2010-11-25
Still no joy, the drive is still not recognized by Ubuntu plugged in to the Ethernet or USB just does not exist.
Am going to try to remove the case and plug it in through my other external H/D case, this worked when wiping a friends corrupted windows drive, if I can work out how it comes apart.

Some days later;  removed the case and swapped the drive over to another case, used "disk utility" to clean format drive, then set it to ext 4 and decided to leave it there, after trying it back in it's old case.
where it still refused to work, guess there mus be something in the hardware.
Works fine in a different case so happy now.

---

