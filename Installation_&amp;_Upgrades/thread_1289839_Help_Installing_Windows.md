---
title: "Help Installing Windows"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by Joseph Schwenker on 2009-10-12
Yes, I know that I am an idiot for asking a question on Windows here.  However, I am not entirely sure of any good Windows forums to ask this question on, and since I use Ubuntu as my primary operating system, I thought that you guys might be able to help.
You see, I was starting to miss Windows a bit, and decided to try to install it and dual boot Ubuntu and Windows, just for the games.  I have Ubuntu installed on my 200 GB ATA hard drive, and an old, abandoned install of Ubuntu 9.04 on my 40 GB IDE Drive.  I have an eMachines T5212.  I inserted my OEM "recovery disk" (they didn't give me an operating disk, just the recovery disk, which has the operating system on it), and rebooted my computer to install Windows.  The loading and installing took forever!  When I had installed Windows before, on top of itself, the loading had been nearly instant, and the install was around 30 minutes to an hour.  This time, the loading took more than a minute, and the install took SEVERAL HOURS.  I had unplugged my 200 GB hard drive with Ubuntu, so that Windows would install to my 40 GB HD.  After the install, and a few reboots, I came to the driver setup screen, where, after the progress bar moved its little way along the screen for a while, Windows gave me an error message that I had not received before.  This error message was asking for a "mouhid.dll" or something like that.  I located the file after two tries and cancellations, and was able to successfully use my mouse and keyboard.  Next, Windows booted up, and the actual Windows setup process was about to start, and Windows shoved a dialoug box in my face.  Internet Explorer was asking for a file called, "msobshel.dll" or something like that.  I clicked on open, and a blank internet explorer windows opened.  I rebooted.  This time, I clicked save, and choose the desktop.  Blank IE window.  Third time, I clicked on cancel, then nothing happened.  I only waited a few minutes.  Should I have waited longer?  Could someone please help me with this?  Should I reinstall Windows again?  What could have caused the system recovery to go SO SLOW?  Why are these error messages appearing?  And again, thanks for putting up with my dumb question posted in the wrong forum.  If you have a suggestion for another forum for me to post this in, then please suggest it!  Thank you!

---

### Post by Mark Phelps on 2009-10-13
I've had complete XP recovery installations take over 8 HOURS! So, having your take hours is not necessarily a sign that anything is wrong.  But the failures you're getting afterward are.

My guess is that the restore didn't complete or there was a failure on the hard drive that prevented writing some files.

At this point, you're most direct approach would be to do the OEM restore again, this time, letting it sit until it's done.  If it fails again, you would need to contact the vendor to see what they suggest.

---

### Post by bruno9779 on 2009-10-13
I would suggest something else.

**_You must have your oem key for this to work and be legal_**

- Download a windows image via .torrent. It has to be the same version as your key is for obviously, and it is legal fair-use as long as your key is a valid key.
- Forget about recovering something that is not there in the first place. Format and reinstall
- google for a good tutorial on how to restore grub

You are likely to save many hours and have a cleaner install (who says that those error aren't caused by damages on the CD-rom?)

---

### Post by Mark Phelps on 2009-10-13
Joseph:

After Googling about your machine, my guess is that the reason the restore failed is that it was designed to use the 200GB drive that came with the machine -- not an alternate 40GB drive that you hooked up.

It's possible that the restore CD is doing a sector-by-sector restore operation and, since the other drive is smaller, starts to fail when it tries to write sectors outside the boundary of the 40GB drive.

Your machine came with MS Windows MCE 2K5 -- same OS the machines had that I restored for some clients.  As I said, it took HOURS for the restore to work.  Also, when done, I had to load a drivers CD.

You're free, of course, to download and hack around with whatever you want, but realize that an image that you "find" on the Net, is likely NOT to be MCE 2005, and almost certainly, will not contain the device drivers needed for your hardware -- especially the 9-in-1 media center device.  You will then be spending HOURS after the installation hunting down drivers for your hardware -- IF you can find them.

So, if you want full functionality restored, your best bet would be to use the eMachines-provided restore CD.

---

### Post by Joseph Schwenker on 2009-10-13
> **bruno9779 said:**
> I would suggest something else.

**_You must have your oem key for this to work and be legal_**

- Download a windows image via .torrent. It has to be the same version as your key is for obviously, and it is legal fair-use as long as your key is a valid key.
- Forget about recovering something that is not there in the first place. Format and reinstall
- google for a good tutorial on how to restore grub

You are likely to save many hours and have a cleaner install (who says that those error aren't caused by damages on the CD-rom?)

So I can just download a .torrent copy of Windows and activate it with my current license key, and that will be legal?  Are you ENTIRELY sure?

---

### Post by Joseph Schwenker on 2009-10-13
> **Mark Phelps said:**
> Joseph:

After Googling about your machine, my guess is that the reason the restore failed is that it was designed to use the 200GB drive that came with the machine -- not an alternate 40GB drive that you hooked up.

It's possible that the restore CD is doing a sector-by-sector restore operation and, since the other drive is smaller, starts to fail when it tries to write sectors outside the boundary of the 40GB drive.

Your machine came with MS Windows MCE 2K5 -- same OS the machines had that I restored for some clients.  As I said, it took HOURS for the restore to work.  Also, when done, I had to load a drivers CD.

You're free, of course, to download and hack around with whatever you want, but realize that an image that you "find" on the Net, is likely NOT to be MCE 2005, and almost certainly, will not contain the device drivers needed for your hardware -- especially the 9-in-1 media center device.  You will then be spending HOURS after the installation hunting down drivers for your hardware -- IF you can find them.

So, if you want full functionality restored, your best bet would be to use the eMachines-provided restore CD.

Would I be able to copy the driver files of of my XP MCE CD Rom?  I just want a bare-minimum install of Windows, JUST to play some of my old games.  I have driver disks for most of my hardware, as a lot of it I have upgraded.

---

### Post by Joseph Schwenker on 2009-10-13
> **Mark Phelps said:**
> I've had complete XP recovery installations take over 8 HOURS! So, having your take hours is not necessarily a sign that anything is wrong.  But the failures you're getting afterward are.

My guess is that the restore didn't complete or there was a failure on the hard drive that prevented writing some files.

At this point, you're most direct approach would be to do the OEM restore again, this time, letting it sit until it's done.  If it fails again, you would need to contact the vendor to see what they suggest.

I am not able to contact eMachines OR Microsoft, as both slam the door in my face because my warranty has expired.

---

### Post by presence1960 on 2009-10-13
> **Mark Phelps said:**
> Joseph:

After Googling about your machine, my guess is that the reason the restore failed is that it was designed to use the 200GB drive that came with the machine -- not an alternate 40GB drive that you hooked up.

It's possible that the restore CD is doing a sector-by-sector restore operation and, since the other drive is smaller, starts to fail when it tries to write sectors outside the boundary of the 40GB drive.

Your machine came with MS Windows MCE 2K5 -- same OS the machines had that I restored for some clients.  As I said, it took HOURS for the restore to work.  Also, when done, I had to load a drivers CD.

You're free, of course, to download and hack around with whatever you want, but realize that an image that you "find" on the Net, is likely NOT to be MCE 2005, and almost certainly, will not contain the device drivers needed for your hardware -- especially the 9-in-1 media center device.  You will then be spending HOURS after the installation hunting down drivers for your hardware -- IF you can find them.

So, if you want full functionality restored, your best bet would be to use the eMachines-provided restore CD.
+1

Plus there are no "legal" or legtimate images of any windows OS on the net for free. They are all pirated versions, and almost to the last one have malware included with the windows OS.

---

### Post by raymondh on 2009-10-13
> **Mark Phelps said:**
> Joseph:

After Googling about your machine, my guess is that the reason the restore failed is that it was designed to use the 200GB drive that came with the machine -- not an alternate 40GB drive that you hooked up.

It's possible that the restore CD is doing a sector-by-sector restore operation and, since the other drive is smaller, starts to fail when it tries to write sectors outside the boundary of the 40GB drive.

Your machine came with MS Windows MCE 2K5 -- same OS the machines had that I restored for some clients.  As I said, it took HOURS for the restore to work.  Also, when done, I had to load a drivers CD.

You're free, of course, to download and hack around with whatever you want, but realize that an image that you "find" on the Net, is likely NOT to be MCE 2005, and almost certainly, will not contain the device drivers needed for your hardware -- especially the 9-in-1 media center device.  You will then be spending HOURS after the installation hunting down drivers for your hardware -- IF you can find them.

So, if you want full functionality restored, your best bet would be to use the eMachines-provided restore CD.

+2

In conjunction, some OEM recovery discs also/may require the use of the recovery partition set up by the OEM.

---

### Post by Mark Phelps on 2009-10-14
> **Joseph Schwenker said:**
> Would I be able to copy the driver files of of my XP MCE CD Rom?  

I already told you what you need to do -- insert the 200GB drive and do the restore to THAT.  It appears that you can not do the restore to a smaller drive.

Your MCE CD is not likely to have all the drivers you need, especially the driver for the 9-in-1 media device that came with the PC.  Also, it will not have the apps that came with the PC for using that device.

As to the license, your machine came with XP MCE 2K5 preinstalled, which means the product key you have is for an OEM version of XP MCE 2K5.  While that key MIGHT work with other versions of XP (i.e., Home, Pro), it's more likely that it will NOT.  So, unless you can find and install the same version of the OS (as was mentioned in an earlier post), you'll most likely run into activation problems after the install.

Again, restoring to the 200GB drive is your best bet.

---

### Post by Don1500 on 2009-10-14
> **Mark Phelps said:**
> I already told you what you need to do -- insert the 200GB drive and do the restore to THAT.  It appears that you can not do the restore to a smaller drive.

Your MCE CD is not likely to have all the drivers you need, especially the driver for the 9-in-1 media device that came with the PC.  Also, it will not have the apps that came with the PC for using that device.

As to the license, your machine came with XP MCE 2K5 preinstalled, which means the product key you have is for an OEM version of XP MCE 2K5.  While that key MIGHT work with other versions of XP (i.e., Home, Pro), it's more likely that it will NOT.  So, unless you can find and install the same version of the OS (as was mentioned in an earlier post), you'll most likely run into activation problems after the install.

Again, restoring to the 200GB drive is your best bet.

+1
Installing Ubuntu to the 40 gig is a lot easier than trying to shoehorn your windows into it. And it will only take about 20 minutes to install Ubuntu once your done. Anyway, it is better to install Windows first, then Ubuntu, grub gets set up right and you don't need to futz with it.

---

### Post by Mark Phelps on 2009-10-14
> **Don1500 said:**
> +1
Installing Ubuntu to the 40 gig is a lot easier than trying to shoehorn your windows into it. And it will only take about 20 minutes to install Ubuntu once your done. Anyway, it is better to install Windows first, then Ubuntu, grub gets set up right and you don't need to futz with it.

While that's true, I thought the OP was asking about how to install Windows -- not Ubuntu.  Once he gets the Windows install done, we can then tackle how to install Ubuntu in a dual-boot scenario.

---

### Post by Joseph Schwenker on 2009-10-16
> **Mark Phelps said:**
> I already told you what you need to do -- insert the 200GB drive and do the restore to THAT.  It appears that you can not do the restore to a smaller drive.

Your MCE CD is not likely to have all the drivers you need, especially the driver for the 9-in-1 media device that came with the PC.  Also, it will not have the apps that came with the PC for using that device.

As to the license, your machine came with XP MCE 2K5 preinstalled, which means the product key you have is for an OEM version of XP MCE 2K5.  While that key MIGHT work with other versions of XP (i.e., Home, Pro), it's more likely that it will NOT.  So, unless you can find and install the same version of the OS (as was mentioned in an earlier post), you'll most likely run into activation problems after the install.

Again, restoring to the 200GB drive is your best bet.

I already have Ubuntu installed and used it for about two months on my 200 GB drive.  Since I would have to switch around disks to get Windows installed, I realized just HOW PROBLEMATIC Windows really is, and figured that if developers develop the worst operating system in the world, then I will make games and develop for Linux.  Thanks for all of your help though!  It's people like you that make my day, not the idiots at eMachines who can only say, "You're warranty is expired.".

---

### Post by Mark Phelps on 2009-10-17
Sorry I couldn't have helped you more -- but it's eMachines that you have to blame for your inability to restore the OS.  They've obviously configure their restore function to require the original 200GB drive, even though, at last usage, you may have required much less disk space.

It would have been a simple matter for them to have configured a 40GB OS drive and install to that, instead of requiring the 200GB drive.  That would have allowed you to do the restore you want -- and it would have also allowed you to do routine OS partition backups from the 40GB partition to the other 160GB partition.

First thing I've always done when acquiring a machine from a vendor is to reformat the drive to shrink the OS partition and use the remaining space to allow for partition image backups.  But, I guess that's too much trouble for vendors to take.

---

### Post by nDevastator on 2010-07-15
Hey guys,

I was brought a T5212 that had the original copy of Windows XP installed over top of and they wanted me to try to restore it to the original manufactures state.  Now that being said they were not sure if it included a restore disk or not.  I was able to find the original restore partition still on the HDD and it appears to still be intact.  The problem is that the "F11" access mechanism no longer appears to be intact and I am somewhat clueless on how I might access and restore using this partition.  Any help on this would be greatly appreciated.

---

### Post by Royle Lindsey on 2010-07-15
[SIZE=2]Hi..[/SIZE][SIZE=2]I cannot open Help files that require the Windows Help (WinHlp32.exe) program..Can anyone help me..Thanks..
[/SIZE]

---

### Post by Joseph Schwenker on 2010-08-06
I believe that the reason why I was unable to install Windows was because the hard drive was not formatted in NTFS.  I had a similar issue on a ten year old HP Pavilion.  I installed Crunchbang on it, but the computer did not let me install Windows again.  Most likely, when I format it in NTFS or FAT32 again, the install will let me.  I guess that Windows just doesn't like EXT3 and EXT4!

---

### Post by Mark Phelps on 2010-08-07
> **Joseph Schwenker said:**
> I guess that Windows just doesn't like EXT3 and EXT4!

MS Windows is unable to read ANY Linux-formatted filesystems.  There are drivers you can load that allow it to work with Ext2 and some Ext3 filesystems, but there are no drivers for Ext4 filesystems.

---

### Post by Joseph Schwenker on 2010-08-10
> **Mark Phelps said:**
> MS Windows is unable to read ANY Linux-formatted filesystems.  There are drivers you can load that allow it to work with Ext2 and some Ext3 filesystems, but there are no drivers for Ext4 filesystems.

So that would make Windows completely powerless to even reformat the drive if it can't recognize EXT3 or EXT4 in a recovery program?

---

### Post by dougalkerr on 2010-08-10
I didn't really want to get in on a Windows problem in a Linux environment but, to try and speed things along...

Have you simply tried the F8 key when the PC is going through the start-up and then opting for system recovery that way.

If you feel you have a file system format problem, use a LiveCD and get to the Partition manager part of the install and opt to format in NTFS or Fat32 and accept the changes BUT stop before actually going on to install Linux.

You will then have the drive formatted with a file system Windows can recognize.

Good luck... but, you should perhaps dump Windows XP altogether and look for an emulator that can run XP games in Linux

OR how about using Virtualbox and installing XP that way as a guest operating system with Linux as the host.

I have done this in the past and have not had any major issues except for the odd USB device but, Virtualbox is getting better all the time.

---

### Post by presence1960 on 2010-08-10
> **Joseph Schwenker said:**
> So that would make Windows completely powerless to even reformat the drive if it can't recognize EXT3 or EXT4 in a recovery program?

NO!!!

Windows can not **_read_** linux file systems. But if you go to computer management in windows (Administrative Tasks) you will see that partitions formatted in linux are there but are listed as unknown. You can format and/or delete these "unknown" partitions from windows Computer Management ( Disk Management). If you start a recovery program the whole disk will be formatted and overwritten to the factory image. Unless your recovery partition/CD/DVD has the option of choosing a partition to put the factory image onto (most do not)

---

### Post by Joseph Schwenker on 2010-08-11
That's a very strange behavior, as all of the machines that I have installed Linux on have had their Windows recovery programs fail.
I might want to add that I seek no further help from anyone, as I now have a new motherboard and powersupply, and am thus incapable of using my restore disc.  
Obviously, recovery programs will not work with EXT3 or EXT4, so my advice to anyone wishing to restore Windows is to format your drive in NTFS or FAT32 (whichever your recovery program requires).

---

