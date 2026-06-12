---
title: "Upgrading to new hard drive on dual boot system"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by CMOS4081 on 2009-07-15
I found similar cases but no simple explanation so here is my post.
 
I have a single sata HDD with a vista and ubuntu for a total of 3 partitions, vista,ubuntu,swap.

I was thinking of going for an HDD twice the side but do not want to go thru the hassle of reinstalling everything. going from an full 500GB to a single 1TB drive.
400B~vista 100~ubuntu/swap. I plan to keep 100GB for ubuntu and the rest for vista 900~ which is were i dump everything as i can access it from linux with ease.

What to you recommend?

I was going to try an acronis and then resize the windows and then boot of usb of ubuntu to rebuild the grub.

both os are 64bit. if that helps.
 
Any advise helps

---

### Post by dstew on 2009-07-15
Is it your intention to replace the smaller drive with the larger on, or to add in the larger drive?

If you are replacing it, you will need to re-install Windows and Ubuntu onto the new drive. You can try the method of backing up, and then restoring to the new drive. That should work. However, some of the boot commands in Ubuntu might reference the partitions by UUID. If so, you would have to change those references to match the UUID of your new drive. That could be a problem booting (check /boot/grub/menu.lst) and mounting partitions (check /etc/fstab). You would also have to re-install grub.

---

### Post by CMOS4081 on 2009-07-15
Thanks for the info.
I know using Acronis will leave me with a working Windows Vista, It seems I'll have to mark the packages for my  Ubuntu and reinstall it. :-k

---

### Post by Mark Phelps on 2009-07-15
If you use the Acronis clone option and do not resize your partitions as part of the cloning (but do it later), I believe that you will find that the OSs will continue to boot using the new drive; however, if you resize the partitions, you're likely to get neither of the OSs to reboot ... at least, that's been my experience.

Also, Vista licensing is tied to the serial number of the hard drive containing the OS partition.  This will automatically deactivate Vista when you boot your new drive and connect it to the network.  It may be possible to reactivate it online -- mine did.  But if that doesn't work, you will have to call the MS Support desk (800 number in India) and get a new product ID through them.  If you have to do that, tell them your old hard drive crashed and you restored to a new drive from external backup.  Don't tell them about dual-boot or running anything other than Vista on the box.

---

### Post by stSpringer2003 on 2009-07-15
I would like to share with, you all, my hard drive clone experience with Ubuntu (Hardy Heron) 8.04.1

I hooked up my two 2.5 inch Hard Drives "laptop size" onto my Dell Dimension 4600 desktop PC. 

I set up the **master drive** "source Drive" which was a 60 gig IDE drive and my **Slave Drive** "Destination Drive" was a 100 gig SATA drive.

The Source disk IDE **was not a dual boot** it just had Ubuntu (Hardy Heron)on it plus I loaded a Netgear wireless WN511B driver on it, and I loaded Flash on it so I could watch youtube videos in firefox, and I enable DVD Playback in Ubuntu, all worked fine so now I wanted to clone this IDE onto a larger SATA drive.

I started by reading this link:

 [http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)



-------------------------------------------------------------
So I followed all the steps from the link running off my Live CD and the first thing I did was run

Partition Editor 

**System-> Administration-> Partition Editor** 

**and deleted all partions on SDB my "Destination SATA Drive"**

and finally got to this command below and hit enter

sudo ddrescue -v /dev/sda /dev/sdb

Well it took about an hour, I did get some errors and then I got another message saying **splitting** **errors**...and I waited

Well it completed and I then looked at my drives with Partition Editor 

**System-> Administration-> Partition Editor**

and that showed a bang mark "yellow triangle with exclamation point" next to SDB ext3

So I powered off my Dell dimension 4600 and made the SADA drive the master drive and disconnected the IDE drive and booted up.

**It worked!**

I didn't have to mess with grub or anything to reset the master boot record it cloned 100%

I haven't tried resizing my partitions yet but plan on it.

Hope this helps...):P

---

### Post by raymondh on 2009-07-15
Another tool should you decide to re-do your installation ...

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Good luck.

---

### Post by carterw65 on 2009-07-15
I used Clonezilla to do mine.

---

### Post by CMOS4081 on 2009-07-16
Again gents thanks for all the experience shared, I hope the knowledge shared helps others as well.
 
Just have to save money for that 1TB HDD on sale!

---

### Post by stSpringer2003 on 2009-07-17
I tried clonezilla and I found that it doesn't like cloneing a larger drive to a smaller drive even though the smaller drive has enough room for the used part of the larger drive.

With ghost I can clone a larger drive to a smaller drive.

Any ideas?

---

### Post by dalexnagy on 2009-09-05
I successfully upgraded my laptop (dual-boot with XP, OpenSUSE) to a bigger HDD using Clonezilla.  I did have some missteps but was finally successful using this process:

1) Installed the new 320G drive in an external USB drive box. 
2) Booted CloneZilla CD and got to the command shell. 
3) Determined which devices were mapped to which drive (in my case,  /dev/sda was my 80G drive and /dev/sdb was my 320G drive) with the LS  command or from messages shown during boot. 
4) Used FDISK (SUDO FDISK /dev/sda) to map the partitions ('p') on my  installed drive.  I noted the order and the type (hex). 
5) Used FDISK on /dev/sdb and defined new partitions in the EXACT SAME  ORDER and with the EXACT SAME TYPE as I saw on the 80G drive onto the  new 320G drive.  I defined the partitions and logical partitions with  larger sizes as I wanted. 
6) Be sure to use the 'w' command in FDISK to write the new partition  table and double check that the partitions are as you want them. 
7) Get back into the CloneZilla GUI and select a device to device  (disk-to-local-disk) cloning operation.  Choose the 'expert' mode so you  can select the 'r' option (to set the file systems to the sizes of the  new partitions) and 'k' to copy over some bytes of the MBR. 
8) Answer all prompts with 'Y' and let CloneZilla copy the data. 
9) Once done, swap the drives and boot. 

XP had to do a CHKDSK on the first boot but didn't find any errors.   Once this was done, XP automatically rebooted again and during the  initialization, loaded drivers for the new disk drive.  All is well with  XP and the new partitions look good (ie, they show with the right sizes). 

Linux booted but halted during the process and asked for verification to  reset a disk id.  I am using 'by-id' to identify devices and the old  disk drive wasn't found but Linux simply asked if it was OK to change  this.  I replied 'Y' and Linux booted great. 

BTW, my SHARED partition is where I store 'My Documents' and it's defined as FAT32(LBA) so I can read and update from either OS.

---

