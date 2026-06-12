---
title: "XP/Ubuntu Dual boot - Three partitions on 1 HDD"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by chippies on 2009-10-06
Hey guys,

Right now my laptop is running only Ubuntu. I want to dual boot my laptop with XP Pro as well, so I can run iTunes. I've read that installing XP first, then Ubuntu is the best method. I've decided to back up my HDD to an external, and reformat the entire HDD and start from scratch.

What I'd like to do is create three partitions on this HDD. One will be for XP, one for Ubuntu, and then one (the largest) 'common' partition that will be shared between Ubuntu and XP. This will house all my pictures, music, videos, basically all my documents that can be used on either OS. 

Can someone point me in the direction of a tutorial on how to set up this common partition? I think I can handle the XP/Ubuntu dual boot install, there's certainly enough material on that topic. It's just this third 'common' partition I'm rattled about.

Also, do you have any suggestions on how to divvy up my HDD space? I'm working with about 230gb total. I was thinking maybe 15gb for each OS, then 200 for the common drive? I'll be primarily using Ubuntu, but occasionally booting XP for iTunes, and a select few other apps I'd rather run on Windows.

Thanks in advance guys, I apologize if I've overlooked any popular tutorials, but all I could find was material on two partition dual boots.

---

### Post by Bartender on 2009-10-06
You're going to end up with more partitions than three.
#1: A primary partition for XP.
#2: A partition for the Ubuntu operating syatem.
#3: A partition for Linux swap.
#4: A partition for shared data.

Here's how I'd do it, especially if I was gonna start from scratch like you say.

Download the latest stable .iso of GPartedLiveCD (GPLCD).  Link below my sig.  Burn slowly (4X or thereabouts) to a good quality CD-R.  This is an .iso, so you need to convert it to a bootable disc, just like you would an Ubuntu download.  When finished, you have a stand-alone partitioner.

Plug in your new HDD.  Boot into GPLCD.  Create a primary partition at the "front" (left-hand side) of the HDD.  Format that partition as NTFS.  Create an extended partition out of the rest of the drive.  Don't worry about doing anything else with that extended partition right now.  The extended is just a "box" for what you'll do later.

Close out of GPLCD.  Boot up with your Windows install disc.  Unless you force it to format the entire drive, it will only recognize the primary NTFS partition.  Install Windows to that partition.  This saves you the hassle of trying to shrink Windows after it's spread itself across the entire drive.

Get out of the Windows install, boot back up, make sure Windows is working.

If so, go back in with GPLCD.  If you just want to auto-install Ubuntu, create a logical partition big enuf for the operating system, swap, and some /home storage.  Format that partition as ext3, or ext4 if you trust the new file structure.  I haven't had any problems with ext4 but lots of folks on the forums are sticking with ext3 for now.  If you want to get fancier than that, with separate /home partitions and such, it's certainly do-able :)

With the remaining space, create a logical partition, formatted as NTFS.  This will be your common storage.  Apply each step as you go, then close out of GPLCD.

Boot up with you Ubuntu installer CD, choose the "Guided" method, and point the installer to that logical ext3 partition.

If you let it install in the default method, GRUB will tweak the Windows MBR so that you get the GRUB screen when the PC starts up and you can choose which OS you want.  Is that what you had in mind?

[Here]("http://ubuntuforums.org/showthread.php?t=1249374") are some screenshots of partitioning schemes.  

If you did what I described above, yours would look like the fourth of the six screenshots.  In that screenshot, the last partition (furthest to the right) is a /home partition.  Yous would be a shared NTFS partition instead.

---

