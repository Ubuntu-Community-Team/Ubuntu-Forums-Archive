---
title: "Dram come true, but with a l;ot of questions!"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by gman2004 on 2005-10-02
I always wanted to install Linux but I never took the time to do it!
Finaly on Oct. 1, 2005 I did it! What an experience has being so far (I haven't been to sleep since I install it). Everything went great, the only things I can't figure out yet and (of course) I need help are three (3) things:
1.   I can't informations of my other two hard drives,
2.   I can't print. I don't know if I need drivers for that (Cannon PIXMA iP300, on USB Port), and 
3.   I downloaded winrar but I can't install it!
Your new body on the Ubuntu world of the free and the brave!

---

### Post by Emerzen on 2005-10-02
Hey Gman, welcome to OSS, I've spent many a sleepless night tweaking system or new apps.  Anyway, here goes some shots at your questions (I'm assuming you're using Breezy):

1.  Go to System->Admin->Disks.  All your (internal) drives are listed there whether mounted or not.  If you want to mount one, select it, select 'Partitions' tab.  Then, under Access Path, find any empty directory and select it, then hit the 'enable' button and the contents of your drive should shortly pop up.  Doing this automatically at boot is a bit more involved, so let me know if you're interested.  If your drive is external, just plug it in and it should be automatically detected.

2.  Don't know about your printer.  You can try to go to System->Admin->Printing and trying to find your printer make/model and installing driver if it's available.  If not, I don't know how to help you on this one.

3.  As for winrar, you typically don't need it.  Open Synaptic and find the packages labeled 'rar' and the 'unrar' packages and install them.  To rar use this package.  To un-rar, just right click the name.rar and select 'extract here.'  

For all newcomers, I recommend going through The Guide [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) from top to bottom.  Keep in mind though, that it's not current for Breezy but is still quite accurate.

---

### Post by gman2004 on 2005-10-03
Emerzen thank you!
I need your help with the hard drives. I got the rar and unrar working and I'm looking for drivers for the printer (it looks like it is a project from what I found out!).
I appriciate you support and I've being reading the support page but you as you know we are like kids, we got a new toy and we have to play with it! 
Thank you again!

---

### Post by Emerzen on 2005-10-03
Hey Gman,

Yeah, it is like a new toy.  I've enjoyed it so much I'm starting to learn Python, and I'm not a computer person (prior to Linux).  Anyway, what's going on w/ your hard drives?  Here's a link that may help w/ your printer [http://www.linuxprinting.org/](http://www.linuxprinting.org/)

-Take care

---

### Post by gman2004 on 2005-10-03
I want the hard drives to be there when I boot.
I do  see them when I Go to System->Admin->Disks, 
but I don't have access to them and it let me "mount" only one.

---

### Post by Emerzen on 2005-10-03
Gman, you should be able to mount both drives simultaneously.  However, you have to mount each drive to an empty directory (this is crucial).  So, if you mounted one drive under directory -- /mnt -- for example, you have to find/create another empty directory for your next disk or unmount the first one.  

As far as mounting at boot, we need a little more info 1st.  Type the following command and post it, if you can:

sudo fdisk -l

This will list all your harddrives and the partitions on each.  Let me know which drives/partitions you want mounted at boot.

---

### Post by gman2004 on 2005-10-03
I did sudo fdish -l and here are the results:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4863    39062016    7  HPFS/NTFS
/dev/hda2            4864        9728    39078112+   f  W95 Ext'd (LBA)
/dev/hda5            4864        9728    39078081    7  HPFS/NTFS
Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4791    38483676   83  Linux
/dev/hdb2            4792        4998     1662727+   5  Extended
/dev/hdb5            4792        4998     1662696   82  Linux swap / Solaris
Disk /dev/hdf: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1        6088    48901828+   7  HPFS/NTFS
/dev/hdf2            6089       19929   111177832+   f  W95 Ext'd (LBA)
/dev/hdf5            6089       12173    48877731    7  HPFS/NTFS
/dev/hdf6           12174       19929    62300038+   7  HPFS/NTFS

hdb is my ubuntu drive,
hdf is my share drive (the one I want to get data from) and
hda is my windows drive with hdd5 I want to share

---

### Post by gman2004 on 2005-10-03
correction hda5 I want to shre

---

### Post by Emerzen on 2005-10-03
Gman,

hda5 is formatted as NTFS.  You will be able to read from this drive (transfer from Windows to Ubuntu) but not write to it (transfer from Ubuntu to Windows).  There are some utilities to allow writing to NTFS but they all entail some risk.  If  were you I would reformat that partition as a FAT32...that way both OSs can read/write to it.

In any case, if you want to leave it as is, here you go (adapted from UbuntuGuide [www.ubuntuguide.org](www.ubuntuguide.org) )

prompt$ sudo mkdir /media/share
prompt$ sudo cp /etc/fstab /etc/fstab_backup
prompt$ sudo gedit /etc/fstab

(A window will pop up, add the following line in there, save it and close it)

/dev/hda5       /media/windows  ntfs    nls=utf8,umask=0222 0       0

prompt$ sudo mount -a

You should can now find that drive under /media/windows via nautilus

---

### Post by Emerzen on 2005-10-04
Correction, you will be able to find the drive under /media/share in nautilus when you're finished and when in the future.

---

### Post by gman2004 on 2005-10-04
I got this error:

mount: mount point /media/windows does not exist

---

### Post by gman2004 on 2005-10-04
I changed 
$ sudo mkdir /media/share to
$ sudo mkdir /media/windows
and I got the error 
mount: /dev/hda5 already mounted or /media/windows busy
but I checked and I see the dir windows, its OK!

Do I do the same for hdf?

---

### Post by Emerzen on 2005-10-04
Hey Gman,

That's my fault.  In the line you inserted into your /etc/fstab file I directed you to used /media/windows when I meant to type /media/share.  It doesn't matter though, you can mount any partiton on any empty directory.  So, when you write to /media/windows in the future, you'll be writing to that partition.  I don't use /media/windows as my mount point as I want to be clear that it's a share partition.  Doesn't matter what you name it though, as long as you're consistent.

---

### Post by gman2004 on 2005-10-04
Emerzen thank you so much. You are a big help.
I rebooted the system and now I see all my drives!
WOW!
I have a question though! I see the .mp3 files but I can't
play them. Can you tell me why?

---

### Post by Emerzen on 2005-10-04
Yep, mp3 is a non-free codec, so Ubuntu can't include support for legal reasons.  As usual, it's not hard to install mp3 capabilities.  Go to [www.ubuntuguide.org](www.ubuntuguide.org) and search for multimedia and follow the directions.  I recommend going through the guide from top to bottom and installing all the multimedia stuff.  If that doesn't get you started let me know.

---

### Post by gman2004 on 2005-10-04
I activated XMMS and I can play mp3 but how can I make XMMS the default player?
Can I save mp3 on the ubuntu partition?

---

### Post by Emerzen on 2005-10-05
Hey Gman,

Yep, you can save any type of file onto Ubuntu, whether you can make any use of it is another matter.  mp3's play fine, so save away.  Files w/ .exe, for example, save w/out a problem, but you can't run them (without windows emulation).

Default player:
System->Preferences->Removable Drives and Media
Select Multimedia Tab
Browse to /usr/bin/xmms

---

