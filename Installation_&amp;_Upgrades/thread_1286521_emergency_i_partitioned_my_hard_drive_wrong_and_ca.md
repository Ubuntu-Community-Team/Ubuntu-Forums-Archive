---
title: "emergency: i partitioned my hard drive wrong and cant access my windows w/ my files!"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by ngage on 2009-10-09
hey,

used gparted from partedmagic to partition my harddrive to dual boot ubuntu but something went horribly wrong. i resized my ntfs windows partition by shrinking down the space and increasing the free space following so that i had like 105 gb following. in the free space preceeding box, i left it at 1 mib.

i then used the unallocated space to set up my ext 4 and swap partitions (setting them both as primary partions). i did not install ubuntu because a problem arose:

I can't access my windows partions with my files! When i right click on that partition and choose information, the warning message is:
ERROR: current ntfs volume is bigger than device size! corrupt partition table or incorrect device partitioning?

when i start my laptop now, it cant boot into windows goes back to dell's bootup screen that asks to start windows normally etc.  I can't see any of my files from parted magic or the ubuntu cd.  I dont care about windows, but i need to recover my files!

---

### Post by PrePenguin on 2009-10-09
Try using F8 and going into safe mode for windows or if your laptop has a hidden restore partition u might beable to recover that way and that button depends on the brand you have..

---

### Post by ngage on 2009-10-09
i am able to choose safe mode for windows from dell's menu but windows still crashes (blue screen of death).  also, when i use the windows vista installation disk that came with my studio 15, to try to repair windows, it doesnt even recognize the windows partion. 

Also, the first time i entered gparted to resize the windows partition, i noticed that it was one of two partitions on the hard drive.  the ntfs partition took up the entire hard drive, and other initial partition was labeled 1 mb of unallocated space. so there was no manufacturer backup partition.  this may have been b/c the first thing i did when receiving the studio 15 laptop was i reinstalled windows so that there was no crapware installed.  the laptop was fine until now


Any other ideas would be greatly appreciated.

---

### Post by Bartender on 2009-10-09
You have a Dell recovery disc, right?  So if worst comes to worst and you can't recover your personal data, at least you can reinstall vista.

If the recovery disc doesn't recognize the vista partition, you may have to wipe the drive with GParted, then create a primary NTFS partition out of all or part of the drive.  The Dell disc "should" install to a clean NTFS partition.

As far as recovering your personal data from a corrupted partition, one way might be to boot from an UbuntuLiveCD or Knoppix CD.  Unless the NTFS partition has been horribly corrupted you should be able to access pictures and documents and etc. and copy them to an external HDD or DVD's or even USB thumb drives if you've got one with enuf capacity.

You could also try slaving the HDD to a desktop PC and see if you can copy off the data that way.

---

### Post by ngage on 2009-10-09
i wasnt able to access the drive from the ubunbut livecd so i just installed ubuntu 9.10 beta 1 on the 100 gb ext 4 drive that i made.  I then tried to access the drive and got this error in the attached screenshot.


it says mount exited with exit code 12: failed to read the last sector, invalid argument etc. failed to mount '/dev/sda1/': doesnt seem to have a valid ntfs, etc.

---

### Post by presence1960 on 2009-10-09
> **ngage said:**
> i am able to choose safe mode for windows from dell's menu but windows still crashes (blue screen of death).  also, when i use the windows vista installation disk that came with my studio 15, to try to repair windows, it doesnt even recognize the windows partion. 

Also, the first time i entered gparted to resize the windows partition, i noticed that it was one of two partitions on the hard drive.  the ntfs partition took up the entire hard drive, and other initial partition was labeled 1 mb of unallocated space. so there was no manufacturer backup partition.  this may have been b/c the first thing i did when receiving the studio 15 laptop was i reinstalled windows so that there was no crapware installed.  the laptop was fine until now


Any other ideas would be greatly appreciated.

Well there is the cause of your problems. If you have a Vista DVD or if you don't download from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") a Vista recovery console CD and follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista.

Next time you resize Vista do not use an outside partitioning tool. Use Vista's disk management utility to shrink Vista's partition. Then use gparted to partition the unallocated space created.

If you follow those instructions you should be able to save Vista without having to reinstall.

There is a well known [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") which is still unresolved when resizing Vista with anything other than it's own disk management utility. The problem is sometimes it works & sometimes it doesn't. I would not want to gamble. just use Vista's disk management utilty to shrink Vista in the future.

---

### Post by ngage on 2009-10-11
ok, presence1960. i installed the vista boot loader from the command prompt of my vista disk, but the computer blue screens and crashes and just takes me to dells start windows normally etc. prompt.

Since windows wouldnt boot, i tried to get ubuntu to boot by following the directions in the same thread u referred me to.  It said to boot from ubuntu live cd to eventually get to terminal.  so from terminal i typed:

$ sudo grub

and i got the error:

sudo: grub: command not found

Then i tried what was supposed to be the next command:
find /boot/grub/stage1
but i got the error: No such file or directory

What can i do now? i cant boot into ubuntu now.
Any more help would be appreciated.

---

### Post by presence1960 on 2009-10-11
> **ngage said:**
> ok, presence1960. i installed the vista boot loader from the command prompt of my vista disk, but the computer blue screens and crashes and just takes me to dells start windows normally etc. prompt.

Since windows wouldnt boot, i tried to get ubuntu to boot by following the directions in the same thread u referred me to.  It said to boot from ubuntu live cd to eventually get to terminal.  so from terminal i typed:

$ sudo grub

and i got the error:

sudo: grub: command not found

Then i tried what was supposed to be the next command:
find /boot/grub/stage1
but i got the error: No such file or directory

What can i do now? i cant boot into ubuntu now.
Any more help would be appreciated.

You can't use the instructions from that thread to restore GRUB because Karmic uses GRUB 2, those instructions are for GRUB 0.97.

If I were you I would use the recovery partition or recovery disks to recover your machine to it's factory image, then use Vista's disk management utility (not gparted, partedmagic, etc) to shrink Vista's partition to make space for Ubuntu.

Also unless you know how to troubleshoot linux on your own I would not install karmic as it is still in testing phase. I would go with 9.04 or 8.04 until the final release version of karmic comes out.

---

### Post by Bartender on 2009-10-11
presence1960 spotted something I'd missed - you used GParted to shrink vista.  Not that it helps you now, but there have been numerous threads on this subject.  Some say you can use GParted as long as you make sure to click on the little "Round to Cylinders" radio button.  Others, such as myself, are erring on the safe side when giving out advice and sticking with the vista partitioner.

Re-reading this thread, I noticed something that *may* explain what happened.  I believe you already had two primary partitions.  You then told the Ubuntu partitioner to create two more primaries.  That was a mistake.  Shoulda made an extended partition, then logicals inside.

I'm wondering if that somehow botched things up.  Theoretically, you can have four primary partitions, but I don't like going right up to the limit.

I'm thinking that slaving your HDD to another PC is your best bet at this point, then wiping the drive and starting over.

---

