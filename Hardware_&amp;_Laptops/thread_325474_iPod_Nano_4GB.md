---
title: "iPod Nano 4GB"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by OMRebel on 2006-12-25
I got a 4GB iPod Nano for Christmas.  I did some searching on the forums, but can't really find one "complete" guide on how to get it working with Ubuntu and amaroK.  Can someone point me in the right direction?  Right now when I plug in the iPod, Ubuntu doesn't seem to see anything.  Works fine when I boot over into Windows, but would rather not have to do that to just copy over some MP3's.  Thanks.

---

### Post by futz on 2006-12-25
You have to install Itunes on a windoze box and run it at least once. That sets up the proper file structure in the Ipod. After that it works just fine in linux.

I have a 2GB Nano.

---

### Post by OMRebel on 2006-12-25
I've done that, and it works fine in Windows.  But, when I connect the iPod I don't get anything.  It doesn't pop up under "Computer", nor does gtkpod see it.  Not sure what I need to do.

---

### Post by mscman on 2006-12-25
According to your profile you're still running Breezy. You may want to consider upgrading to Dapper 6.06 (LTS) for some added functionality. I can't remember how well Breezy dealt with automounting flash drives.

---

### Post by futz on 2006-12-25
> **OMRebel said:**
> I've done that, and it works fine in Windows.  But, when I connect the iPod I don't get anything.  It doesn't pop up under "Computer", nor does gtkpod see it.  Not sure what I need to do.
That's odd. Do other usb devices mount properly? Sounds like something wrong with your usb.

The Ipod mounts as a drive. You can't, unfortunately, just drag songs to it tho (well you can, but they won't play). You can use it as storage if you wanted to. You have to use a program like Floola or Amarok or others to put music on the Ipod.

---

### Post by OMRebel on 2006-12-25
All of my other USB devices work fine in Ubuntu.  USB keyboard, USB mouse, USB 802.11b wireless, USB printer, USB scanner, etc...  

Is there a command I can run in terminal to see if it even sees my iPod?

---

### Post by OMRebel on 2006-12-25
@ mscman
I'm actually running Eft.  I'll update my profile to reflect that.  Should have mentioned that...sorry.

---

### Post by OMRebel on 2006-12-25
Anyone have any suggestions?

---

### Post by Azakus on 2006-12-25
Plug in your iPod and run ```
sudo lsusb | grep "Apple"
``` and see if it pops up with anything.

---

### Post by OMRebel on 2006-12-26
Okay, it sees it now!  What I did was reboot with the iPod actually attached (before I was just attaching the iPod after the reboot..oh well).  Then I did as you suggested, and got:

Bus 003 Device 004: ID 05ac:1260 Apple Computer, Inc. 

So, it now sees it.  

I checked under "Computer", and it lists it as "Apple iPod Music Player".  I then tried to mount it, and I got an error.  I'm attaching the screen shot to this post.

So now it looks like a problem with just mounting the device.  What will be my next step?

---

### Post by OMRebel on 2006-12-26
Some additional info:

brad@brad-ubuntu:~$ sudo mount -t vfat /dev/sdb /media/ipod
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

brad@brad-ubuntu:~$ dmesg | tail
[17180728.524000] UDF-fs: No partition found (1)
[17180728.580000] Unable to identify CD-ROM format.
[17180728.584000] FAT: bogus logical sector size 2
[17180728.584000] VFS: Can't find a valid FAT filesystem on dev sdb.
[17180728.588000] hfs: unable to find HFS+ superblock
[17180728.588000] hfs: can't find a HFS filesystem on dev sdb.
[17180728.592000] VFS: Can't find an ext2 filesystem on dev sdb.
[17180728.596000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[17180785.860000] FAT: bogus logical sector size 2
[17180785.860000] VFS: Can't find a valid FAT filesystem on dev sdb.

---

### Post by OMRebel on 2006-12-26
I added the following to my /etc/fstab:
/dev/sdb2 /media/ipod vfat iocharset=utf8,umask=000 0 0

That got it mounted, and gtkpod can now read the iPod. 

Now the problem is that amaroK won't see it.

---

### Post by OMRebel on 2006-12-26
Sorry for making so many posts.  Amarok is now reading it, but I can't play the music.  I get a message on the bottom of Amarok saying, "Some media could not be loaded (not playable)"  

I have Amarok v 1.4.3

Also, whenever I select a song, no information is displayed on it.  Am I missing something?

---

### Post by Azakus on 2006-12-26
For Amarok, you have to install the ipodslave plugin.
```
sudo aptitude install ipodslave
```

---

