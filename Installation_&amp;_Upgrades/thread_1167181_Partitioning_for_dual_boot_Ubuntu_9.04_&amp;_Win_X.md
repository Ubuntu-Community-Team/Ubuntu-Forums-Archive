---
title: "Partitioning for dual boot Ubuntu 9.04 &amp; Win Xp"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Wayne Twine on 2009-05-22
Hi

I'm new to Linux/Ubuntu, but ready to take the plunge and install Jaunty as a dual boot with the existing Windows XP on my HP laptop.  However, I need guidance at the partitioning stage of the Ubuntu installation - I am not a techie.

My HP has a 88 GB c hard drive, and a 6 GB "recovery" hard drive (h drive).

When I install Jaunty from CD and get to the partitioning screens,the "Prepare disk space" shows MS Windows XP (/dev/sda1) 88GP (blue), and Windows NT/2000/xp (/dev/sda2) 6 GB (green), with no unallocated space.

I select "Specify partitions manually"

The "Prepare partitions" shows sda1 (ntfs) 88 GB (green) and sda2 fat32 5 GB (orange)

This is where I get stuck - the "Prepare partitions" is not have the the simple sliding partition bar I have seen on screen shots in tutorials for 8.04.

I assume I need to repartition the ntfs drive (sda1).  Do I check  "format" for that drive?  Then what?

Sorry if I'm being thick, but this is all new to me.

Cheers

---

### Post by hal8000 on 2009-05-22
You first need to make space on your Primary NTFS partition to install Ubuntu. First thing to do is backup all your own work and important documents, then defrag your C drive from windows so that all data is moved to the front of the partition.

Now click this link and print it out:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Then load the live Jaunty CD, go to System, Partition editor and shrink the largest partition, this will be your windows C: drive. Follow the instructions on the link. A minimum space of8G should be sufficient. After resizing, reboot into windows and let windows chkdsk do its thing.

Then reboot the Jaunty CD and this time choose to install, it will see the newly created space and offer to install into the space for you. This is the easiest way to install.

---

### Post by logos34 on 2009-05-22
No, you don't want to format sda1!

Start over and either use the ['Guided--resize' option]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3")

or follow [this guide]("http://mywebsite.bigpond.net.au/dfelderh/p23.html") to use Gparted to shrink windows manually.

Make sure windows in defragmented beforehand.

---

### Post by Wayne Twine on 2009-05-22
The problem is, Jaunty "prepare disk space" does not have a "Guided" option as depicted in
the screen shot in the link (probably Hardy) you suggested.

---

### Post by logos34 on 2009-05-22
ok, whatever...then just quit the installation part and go back to the desktop.  Use gparted to shrink windows (system>admin>partition editor)

---

### Post by Wayne Twine on 2009-05-22
Hal8000 and Logos34

I tried running Gparted but it won't allow me to resize the NTFS partition- sliding bar arrows don't respond and "resize/move" button at bottom is greyed out.

Attached (I hope) is a screen shot

---

### Post by Fourcultures on 2009-05-25
Wayne - I'm also experiencing this mismatch between the prepare partitions screen people talk about and the one I actually see when I attempt to install Ubuntu 9.04. I think this [help information]("https://help.ubuntu.com/9.04/switching/installing-partitioning.html") makes some sense of the new screen options. But where it says "'right click on the windows partition... select resize' it's not obvious how you do this. 
I'll post something else when I get past this bit...

Fourcultures

[https://help.ubuntu.com/9.04/switching/installing-partitioning.html](https://help.ubuntu.com/9.04/switching/installing-partitioning.html)

---

### Post by Fourcultures on 2009-05-25
...So to continue, trying to resize using GParted I had exactly the same problem as you describe, with Gparted not allowing me to shrink the ntfs partition. So I checked whether it was mounted and therefore already in use: it wasn't (as I expected, since I'm doing the installation off the Ubuntu live CD on a USB stick, which shouldn't be mounting my hard drive). Then I attempted to unmount the other partition that was available on the tab at the top right hand corner of the GParted window (You click the downwards pointing arrow to make it visible). On my computer this is labelled /dev/sdb. It couldn't be unmounted because it was in use (as I also expected, because this is the partition on my USB drive). But here's the interesting thing: that seemingly pointless procedure unfroze the options for the ntfs partition on the hard drive. No idea why, but it worked. From there it was easy and obvious how to resize the ntfs partition, as per existing documentation. 

Don't know if this could help you , but mysteriously it worked for me... there's probably a perfectly logical explanation.

Fourcultures

---

### Post by linuxfanboy on 2009-05-25
> **Fourcultures said:**
> ...So to continue, trying to resize using GParted I had exactly the same problem as you describe, with Gparted not allowing me to shrink the ntfs partition. So I checked whether it was mounted and therefore already in use: it wasn't (as I expected, since I'm doing the installation off the Ubuntu live CD on a USB stick, which shouldn't be mounting my hard drive). Then I attempted to unmount the other partition that was available on the tab at the top right hand corner of the GParted window (You click the downwards pointing arrow to make it visible). On my computer this is labelled /dev/sdb. It couldn't be unmounted because it was in use (as I also expected, because this is the partition on my USB drive). But here's the interesting thing: that seemingly pointless procedure unfroze the options for the ntfs partition on the hard drive. No idea why, but it worked. From there it was easy and obvious how to resize the ntfs partition, as per existing documentation. 

Don't know if this could help you , but mysteriously it worked for me... there's probably a perfectly logical explanation.

Fourcultures

Weird...I boot from cd not usb so not sure this will work but can you explain what you did in detail? I thought that area was where you mount not unmount....but new to ubuntu so maybe im wrong.

I also have same issue as a lot of you....starting to think its a bug inside jaunty's live cd or the partitioning software it uses...my thread with the problem here.

[http://ubuntuforums.org/showthread.php?t=1169448](http://ubuntuforums.org/showthread.php?t=1169448)

---

### Post by Fourcultures on 2009-05-27
Suggestions:
 
1) Ensure that your hard drive isn't mounted. If it is still mounted, GParted can't re-partition it. [Unmount it]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-unmount-partition"), then try again.
 
2) [Refresh all devices]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-refresh-device"). If GParted's view of your hard drive is somehow frozen, this might fix it.
 
3) Do what I did and click on the downwards pointing arrow near the top right corner of the GParted window, as in this [screen shot ]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-when-you-start")from the manual.
 
This will reveal if there are any other available partitions on any other devices (ie my flash drive, /dev/sdb). I checked to see if it was mounted and sure enough, it was. But this didn't matter, since I wasn't intending to re-partition the flash drive anyway. The point is that when I clicked the button at top right again to go back to a view of the internal hard drive, I found it was suddenly mysteriously able to be re-partitioned. I suspect some kind of automatic refresh took place (see 2 above). You could try this, but I guess that because you're using a live CD there won't be any other partitions available, in which case...
 
 
3) If the drive can't be unmounted and refresh has no effect and you have no other 'hidden' partitions to look at, try using the [live CD of GParted]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-acquire-livecd"). This automatically unmounts everything, and it may or may not help unfreeze the re-partitioning process, but I haven't tried it.
 
4) If all else fails you could try installing off a live USB stick, like I did. Don't think this would make much difference, but at least you'd be doing exactly what I did, and actually the live flash drive is useful for using Ubuntu on anyone's computer.
 
5) Don't give up. I'm now enjoying using Ubuntu which is on the whole far superior to Windows. It has so many nice extra touches. My wife saw me using it and now she wants me to dual boot her Vista machine.
 
Let us know how you get on!

---

### Post by zman58 on 2009-05-31
I have seen this exact same problem as I am just installing Jaunty on a brand new HP G60 (HP-244DX). AMD Athlon X2 with Nvidia 8200 graphics, 3G RAM, and 250 GB hard drive. I thought it was a good buy at $450 from Best Buy. It has Vista Home on it and I want to provide dual boot with Ubuntu.

When I first tried (quick test) Ubuntu live CD, before I ran Windows Setup for the first time, it looked like I could easily re-size the NTFS partition, BUT I canceled the install because I wanted to first backup system and setup the Windows before installing Ubuntu. The slider on the partitioning tool for the re-size operation under Ubunt WAS THERE at that time.

I first did a complete system hard drive backup to an external USB drive using Ghost--just in case.

After I completed setting up Windows Vista for the first time, then went back into the Ubuntu Live CD I was no longer able to re-size the NTFS partition :( . The slider was no longer there indicating that ALL of the NTFS partition was in use (reserved?). My suspicion is that Microsoft has done something during setup with the file system that prevents the Linux partition tool from realizing that NTFS could be resized. ...this is only a suspicion, not proven at this point. Anyways continuing...

Gparted would not allow me to resize the NTFS partition. Ubuntu would not allow me to resize the NTFS partition. I was basically stuck. About the only thing I could do was to install Ubuntu over top of the OEM Windows restore partition--something I did not want to do.

After some hunting around, I discovered that Windows Vista has a partition re-size utility with the computer management tool "disk management" or whatever it is called. I first defragged the NTFS partition which took nearly 4 hours on this brand new system that I just ran Windows setup and updated!!

Vista is an absolute drive hog. I turned off the Sytstem Restore (shadow copy) which provided an additional 70 GB of unused drive space...

After all of this fussing around with Windows, I was finally able to use the disk management tool in Vista to reduce the NTFS partition about 120 GB. This actually only took about a minute (surprise!).

OK, Now I went back to the Ubuntu 9.04 Jaunty desktop live CD and was able to install Ubuntu into the free space on the system hard drive.

I am now making some additional adjustments to get everything I need set up with Ubuntu 9.04 on this brand new HP laptop. I plan to give it to my son for graduation gift and to use at College in the fall.

Dual boot on the G60 is now working great.

If it were for me I would have first removed Windows from it completely and saved myself about 6 hours of fussing around. :)

To summarize:
It looks like you will need to get a Windows based partioning tool to reduce the NTFS partition to create empty drive space for Ubuntu. I have seen some free ones, but because Vista already had one I did not have to go that route.

---

