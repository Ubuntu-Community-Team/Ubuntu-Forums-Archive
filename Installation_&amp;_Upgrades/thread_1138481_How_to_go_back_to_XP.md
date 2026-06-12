---
title: "How to go back to XP"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Pilot_Neil on 2009-04-26
I had a hard disk with XP on but decided to install Ubuntu. I am a noob with Linux so no idea what I was doing.
 
Basically I want to put XP back but when I boot into the XP install it says I have no hard disks installed! Well I must have because I can boot into Ubuntu. 
 
How can I get back to XP? I read on MS Support that if I have a linux boot disk I can run fdisk and delete linux boot records etc which will get my disk back. This all sounds great but where do I get a Linux boot disk with fdisk on it? I've done some searching around and theere seems to be too many options and I have no idea what to use..
 
Can someone help me? My computer is as good as dead at the moment :(
 
Thanks.

---

### Post by OpenSourceFuture on 2009-04-26
Reformat the Linux partition(s) to FAT32 and they will be viewable when you boot to windows.

---

### Post by Stavro on 2009-04-26
You say you are new and don’t really know what you did, so based upon that I would ignore the previous advice completely. At this time, you don’t want to format anything, it may not be a solution at all.

When you boot the computer, do you have a menu that gives you the choice of using Windows XP or Ubuntu? By default, Ubuntu is at the top, you will be looking at the end of the list, probably the last entry for Windows XP.

---

### Post by Pilot_Neil on 2009-04-26
I don't get a menu it just goes straight to Ubuntu unless I boot from CD to the XP install.  So its like XP does not exists at all any more.

---

### Post by Sub101 on 2009-04-26
Do you know if you installed Ubuntu onto a partition on the whole disk?

Can you see any files from the XP installation?

---

### Post by Stavro on 2009-04-26
Then you’ve probably chosen every default option out of the book. It may surprise you to learn that the default behaviour is to completely erase the primary hard disk. Actually, I think this should be changed when an existing Operating System is present. Linux doesn’t have to adopt anti-competitive strategies as well.

Did you have any important stuff on XP? If so, did you do a backup of your files? From here on you’ll need your original XP install CD I’m afraid.

---

### Post by Pilot_Neil on 2009-04-26
I think I did a install over the whole disk so XP is gone for ever.  This is not a problem as I had backups done same day and I do have the XP install CD.  

I can't see any Windows files.

---

### Post by Stavro on 2009-04-26
If you can be certain you erased the whole disk, there is no point wasting time if you want to go back to XP. Simply, insert the XP install CD and follow the instructions from there. Your computer will highly likely be already setup to boot from CD as you have managed to install Ubuntu in the first place.

---

### Post by zenithdave on 2009-04-26
> **Stavro said:**
>  It may surprise you to learn that the default behaviour is to completely erase the primary hard disk.

Are you sure about that? i thought the default was to resize the windows partition :confused:

However i think the installer should tell people to go back to windows and defrag XP partition before resizing it.

---

### Post by Stavro on 2009-04-26
Don’t forget, the XP install CD is probably decidedly out-of-date, once you’ve connect it to the internet and registered, run Windows update as soon as possible.

---

### Post by Stavro on 2009-04-26
> **zenithdave said:**
> Are you sure about that? i thought the default was to resize the windows partition :confused: 

Quite positive, I’ve seen this with Ubuntu 6.06, 7.04 and Xubuntu 7.04 as well as Xubuntu 7.10 I believe, but can't be certain about that one. I’ve long thought this behaviour is crazy but never complained here on these forums.

---

### Post by Pilot_Neil on 2009-04-26
The problem is I run the XP install CD and when it says press enter to install Windows I get a message saying no hard disks are detected please connect them with power etc.  The disk is fine obviously as I am in ubuntu now writing this post.

Thanks for your help so far guys.

---

### Post by Stavro on 2009-04-26
I have to say that sounds really strange, anyone with any ideas? Which version of Ubuntu is it? Perhaps it’s the EXT4 filesystem, though I doubt it, I believe the Windows installer does not concern itself with the existing structure of the disk.

---

### Post by Stavro on 2009-04-26
If it can be proven that EXT4 causes the Windows installer to not see the hard disk, then get yourself this freeware disk shredder applet from another computer and create a bootable CD.

[http://www.miray.de/products/sat.hdshredder.html](http://www.miray.de/products/sat.hdshredder.html)

---

### Post by RichardG891 on 2009-04-26
> **Pilot_Neil said:**
> The problem is I run the XP install CD and when it says press enter to install Windows I get a message saying no hard disks are detected please connect them with power etc.  The disk is fine obviously as I am in ubuntu now writing this post.

Thanks for your help so far guys.

Yes, XP should detect the presence of the drive even it can't make sense of it. However, you could try booting the ubuntu **CD** in live mode and then use the partition editor to check the disc and delete the linux partition, and then either leave it as free space or re-format to NTFS.

---

### Post by wsonar on 2009-04-26
> **Pilot_Neil said:**
> The problem is I run the XP install CD and when it says press enter to install Windows I get a message saying no hard disks are detected please connect them with power etc.  The disk is fine obviously as I am in ubuntu now writing this post.

Thanks for your help so far guys.


Is this a laptop?

I've seen some alien ware where they need raid drivers installed for XP install to see the HD

IF ubuntu install see's it but XP dosen't this could be the case

do you have an OEM disk?

---

### Post by wsonar on 2009-04-26
I had a buddy that just wanted to reinstall XP never had ubuntu on the system he could boot into XP but the xp install would not see his HD it was for what ever reason came as a raid so XP install would have needed these drivers for some odd reason tho xp only give you the option to get these from a floppy unless you make a custom oem install or network install

installing ubuntu had no problem seeing these drivers as well as vista I believe

---

### Post by Pilot_Neil on 2009-04-26
I have an XP oem disk to use.  I am not using a laptop.  I tried that disk shredder thing and it gets to 84% and failes with unable to read disk.  
 
With regard to riad drivers the disk was part of a two disk raid array before I made it standalone for the Ubuntu install.  Maybe that is where my problem started.
 
The person who suggested "However, you could try booting the ubuntu **CD** in live mode and then use the partition editor to check the disc and delete the linux partition, and then either leave it as free space or re-format to NTFS."  Can you explain exactly how I do this?

---

### Post by Stavro on 2009-04-26
I think you'll find the partition editor on the application menu somewhere, probably in system tools or something. It’s called Gparted.

---

### Post by wsonar on 2009-04-26
where you able to disable the raid in the bios?

---

### Post by wsonar on 2009-04-26
> **Stavro said:**
> I think you'll find the partition editor on the application menu somewhere, probably in system tools or something. It’s called Gparted.


gparted is not istalled by default on my system

if it is not installed it can be installed from add/remove

or sudo apt-get install gparted from a terminal

---

### Post by RichardG891 on 2009-04-26
The person who suggested "However, you could try booting the ubuntu **CD** in live mode and then use the partition editor to check the disc and delete the linux partition, and then either leave it as free space or re-format to NTFS."  Can you explain exactly how I do this?[/QUOTE]

Sorry, meandered off to a different thread for a moment....

The ubuntu disk you used to install will also run in live mode - once you've chosen the right language, select "try ubuntu without any change to your computer"... and let it boot.

The partition editor is in System > Administration > Partition Editor

hope this helps

---

### Post by Pilot_Neil on 2009-04-26
I'm in the partition editor and managed to get about 1.5 gig free space by getting rid of a partition.  I can't seem to get rid of the main one or resize it.  It won't let me unmount it.

---

### Post by wsonar on 2009-04-26
I'm going to have to say no matter what partions are on the drive I don't feel that's the reason XP install is not seeing the drive

---

### Post by Pilot_Neil on 2009-04-26
May be this is more of a XP problem then.  I am going to have a look round to see if I can find something which can remove the partitions or trash the disk so XP will recognise it.

---

### Post by Pilot_Neil on 2009-04-27
I have managed to get XP back and working.  Things is to do that I had to set everything back how it was.  I had to plug my hard drives back into their RAID SATA ports, Set RAID in the BIOS, create an array at boot and then specifiy the raid drivers on floppy during XP setup.  
 
I am going to try ubuntu again shorty and will see if it will automatically adjust my windows partition which is using all of the drive.

---

### Post by Stavro on 2009-04-28
Cool, better luck with Ubuntu next time. Nice to see you’ll give it another go. Let me know please whether the installer for 9.04 also defaults to erasing the whole disk, I think it does unfortunately. After all those things you described to get XP back again, seems like you’re not so much of a beginner after all!

---

### Post by Scooby1 on 2009-04-28
Too bad I didn't get here earlier, this was the exact reason I switched to linux! 

Had a dead hard drive a couple years ago and my XP install CD wouldn't recognize my new SATA drive without a floppy with SATA drivers. Too bad I dont have a floppy drive, seeing as the technology is obsolete. I couldn't jsutify spending $20 on a floppy drive and then trying to find a store that actaully sells floppy disks, so decided to give Ubuntu a try. Well, ubuntu installation CD recognized SATA drive right off the bat... Couldnt belive microsoft would force me to use a floppy to install anything in this day and age, how hard is it to fit a SATA driver on the CD-ROM? Hence my microsoft hate began....

---

