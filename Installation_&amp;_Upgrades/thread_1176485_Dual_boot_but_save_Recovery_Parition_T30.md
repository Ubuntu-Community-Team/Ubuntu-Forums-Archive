---
title: "Dual boot but save Recovery Parition T30"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by emeraldgirl08 on 2009-06-02
Hi. I had to do a System Reset yesterday which meant restoring my laptop to factory preset. I also had cloned an HD before that to a faster drive. The old installation of Ibex was my first and in my haste to install it I did not read the fine print on how not to overwrite the MBR!

Needless to say I winded up destroying my Rescue and Recovery Partition. A friend of mine sent me copies (4 CD's) to restore my comp which meant wiping out everything on the HD. Now that it's up and running great I'd like to install Jaunty and keep my Rescue and Recovery partition (press F11 for restore at startup).

**I don't want to erase the MBR like last time!!!** It took me from noon to bedtime last night to replace and configure the XP to a somewhat decent state! I already have an fdisk -l report but it's from a liveCD run of Jaunty. Here it is:

[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa266a266

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10107    76408888+   7  HPFS/NTFS
/dev/sda2           10108       10337     1738800   1c  Hidden W95 FAT32 (LBA)
ubuntu@ubuntu:~$ [/I]

How do I begin to install Jaunty? I have a bunch of ISO's I burned that include Gparted Live 0.4.5.2, Super Grub Disk 0.9797, System Rescue CD 1.2.0, Clonezilla (won't be needing that one), and have all three distros of Ubuntu starting from 8.04. I'd like to have a partition for Windows, Ubuntu, and a shared FAT32 folder for music, videos, etc.

thanks.

---

### Post by quixote on 2009-06-03
Well, it makes it easy that you're starting clean :D

You have your big Windows boot partition, sda1.  That's the one you'll be carving some free space out of.  sda2, if I understand it right, is your Recovery partition.

So, to install jaunty, all you need to do is carve out some of the free space on the drive for that.  You won't need gparted on a separate disk or anything.  It's part of the liveCD.

Boot from the liveCD.  When you get to the install screen that asks whether to use the whole disk (NO!), or guided install (also no), choose "manual."

Then decide how big you want your jaunty partition to be.  Note: it's clever to have a separate /home partition because then you can upgrade the OS without losing your particular settings or other files or programs in /home.  However, you can only have 4 primary partitions on a physical device, and you've already got 2.  So do the following:

Let's say you want 5GB for jaunty itself, 10GB for /home.  You also want, say 50GB for data.  Assuming you have 65GB with no files on it which shows up as empty on sda1, select that to delete and turn into "free space".

Then select it to be formatted as an extended primary partition.  

Within the extended partition make three logical partitions: 5GB with ext3 filesystem and a mountpoint / (ie that's where jaunty itself goes), 10GB with ext3 and a mountpoint /home, and the final 50GB with a vfat filesystem.

Linux also needs swap space.  Best is about 1.5 to 2 times the amount of RAM your computer has.  I think with the newer ubuntus you don't have to be specific about swap space.  It apportions swap space on the fly.

When you proceed, it'll tell you which partitions it will format.  Make sure sda1 and sda2 are NOT checked.  Carving free space out of sda1 should not lead to the whole thing being formatted.  The partitions to be formatted should have new numbers, like sda3 for extended, and sda5, sda6, sda7 for the others, or something similar.

Good luck, and tell us how it goes!

---

### Post by emeraldgirl08 on 2009-06-03
I forgot to mention that I winded up installing XP Pro three times on the same drive! Well I don't know if it installed three times but there was the M$ boot program and it had three Windows XP Professionals!

Yes I freaked out and luckily had my PDA which I could connect to wifi with and message my friend. He told me I needed a CLEAN HD to install the recovery partition and OS on.

:p

I winded up using KillDisk to zero out my HD and start over again!

It was a pretty scary mess for awhile :D

So I'm now thinking of that old HD I replaced. I'm thinking of wiping that drive clean and installing Jaunty on that instead. In Thinkpads you have your Ultrabay that you can put a DVD/CD drive, Floppy Disk, Extra Battery, or second HD in. I can get the Ultrabay HD adapter for twenty dollars. 

And you can boot from this bay also! 

I'm considering that avenue b/c if I'm not mistaken I cannot boot a USB external drive from a Thinkpad T30. I've tried it with my old Ibex partition in an external enclosure. It didn't work. I went into BIOS and checked the USB config and it's for Floppy Disk. Never heard of a Floppy Disk USB. I'm just bouncing ideas around here. It seems like a nice idea b/c with the last dual boot I had things slowed down noticeably in Windows and it took forever to get into a user account in Windows! I still use Windows sometimes hence the dual boot. 

What do you think is best? If someone has the external drive boot then I want to hear how you did it! If not then the adapter I will purchase sometimes next week.

Whoops almost forgot to thank Quixote. THANKS :)

---

### Post by quixote on 2009-06-03
Booting from a usb-connected hard drive has some unexpected effects.  Unfortunately, I don't remember for sure what they were.  I think maybe that the USB-HD is first in the boot order, but Windows on the internal HD wants to be first and the system breaks down.  Anyway, as you saw already, there are Issues.

Putting a drive in the bay shouldn't cause any problems, though, and sounds like the best solution.  When you're installing: make sure you're installing on the correct drive (size is usually the easiest way to tell apart the cryptic drive designations).  And make sure you're NOT formatting your Windows or your Recovery partitions.

---

### Post by emeraldgirl08 on 2009-06-03
> When you're installing: make sure you're installing on the correct drive (size is usually the easiest way to tell apart the cryptic drive designations). And make sure you're NOT formatting your Windows or your Recovery partitions.
That's pretty much how I determine which drive is what lately. Formatting the wrong drive should not be a problem now that there's a size difference for discernment. 

I'm going to go for the Ultrabay HD. **Things just work better for me when the OS' are in separate HD's!** I really don't feel like shrinking and resizing Windows again. I'll just leave the bloated pig alone in it's new 5400 rpm glory! Considering how crappy that worked in the old 4200 it's working better with this one.

The Linux will find a home in the old 4200 rpm HD. I figure by the time the new LTS comes around I'll have enough spare change to buy a 100 gb + HD for Linux :)

Sound like a plan???

:KS

---

### Post by quixote on 2009-06-05
Sounds like a plan :)

The stuff about having separate partitions for / /home and a vfat one for data would still apply on a separate drive, if you wanted to do it that way.

At the rate HD drive prices are falling, you'll be able to pick up a terabyte at the Mallwart by September!

---

### Post by emeraldgirl08 on 2009-06-06
Quixote. I already wiped my old 40gb HD with Killdisk. I couldn't wait to install Jaunty. T30's will not boot from a USB enclosure (as far as I know). I came up with a happy medium for now. 

I ordered the Ultrabay adapter and figured why not install Jaunty on that 40gb HD! What would it hurt? I could just killdisk it again if I flubbed up. I was very scared in the beginning. After all the work it took to restore my XP Pro I really didn't want to wind up zeroing out my new HD. I tried killdisking the old HD in it's enclosure.

It was a no go.

It wasn't recognized at all. The only devices I saw were my Seagate 80gig and my Ultrabay device (the comp was calling it a floppy drive). I figured why not just take the Seagate out and put the old 40gig in the laptop. Five minutes later killdisk was wiping out the old Hitachi. By that point I was brainstorming. Okay I had these ISO's I had burned and was pretty sure one would work in my situation. I figured use Gparted and create a FAT32 partition. This would be the place I could put "whatever" for migration between the two OS'. 

It worked.

I installed Jaunty and directed it's installation to the largest free space on the drive. The FAT32 remained untouched. I let Jaunty do it's thing and went to wash dishes. By the time I got back it was installed and needed updates. 

I now got it updated and saw that upon restarting my option for F11 as gone...AGAIN! By this time I had to go to work. So I'm at work thinking "SOB!" I really hope when I put that Windows HD back in my laptop it works!!! I just got home and put the 80 gb back in...it works :)

I didn't see the F11 at the very beginning under the IBM logo but after that left there was a prompt to press F11 for recovery. All in all a good deal! When that adapter gets here next week or possibly the week after (it's coming from China...yeah) the HD will have Jaunty and my media partition already installed :)

---

### Post by quixote on 2009-06-06
A pretty good example of perseverance paying off :D !

One thing to think about when your new bay arrives: if I understand it right, you installed Jaunty on the old HD when the Windows HD was not connected, so it has no way of knowing about its existence.  I would expect that when both drives are in the machine, you won't get a grub multiboot menu.  That's tedious, but there are ways to fix that.  I've used the info [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), but I'm not sure it applies if your linux is on a separate drive.  There's also something that looks pretty slick called [Supergrub]("http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems") (download [here]("http://forjamari.linex.org/projects/supergrub/")) that you may want to have a look at.

Or, I guess, you could just reinstall Jaunty once you have both drives in your computer. (But that seems too easy, no?  And not so good if you've already installed a bunch of stuff by the time you have the new bay.)

(*Everything* is made in China.  I ordered a hummingbird feeder which I saw was made in the USA, and I nearly fell off my chair.)

---

