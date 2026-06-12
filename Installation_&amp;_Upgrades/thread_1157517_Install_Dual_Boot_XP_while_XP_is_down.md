---
title: "Install Dual Boot XP while XP is down?"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by runningeagle on 2009-05-12
Hello, new to Linux here,
 
I am reading how to install Kubuntu
but I am confused as to which ways will allow me to keep Windows intact with all my files. I have read many install guides, but I don't know which ones are clean install and which ones leave Windows intact. I have read guides that say to first use a GNOME partitioner program, and others that say to go straight to install, and I am confused what will give me all my files from Windows. 
 
Here is my story:
Windows recently had a c0000218 error and would not start up in any way. Because I desperately needed to print, a friend suggested installing Kubuntu temporarily. The desperate need to print turned out to be null as I had the file in e-mail.
I would like to have kubuntu dual boot with Windows XP x64 so that nothing is changed when I get a Windows disk to do a repair install. Everything important is already backed up on CDs and e-mail, but I still want to keep Windows intact as it still has many Would-Like-to-Keep-but-not-Absolutely-Necessary files. 
I have two hard drives in my machine and Windows is on one of them. I have NTFS file system. The hard drive without Windows has a lot of space, so I want to install Kubuntu there. The drive windows is on has only 5 gb free (I tried to delete unnecessary files using Kubuntu in livecd mode, but I could not delete anything large).

I ran GParted from the livecd but it would not work. I did chkdsk in the Windows Recovery Console, but I can't run Defrag without starting Windows.
 
When I tried Ubuntu's livecd, it went to the desktop but there were no progam toolbars, and none of the icons would work. 
 
In summary,
how do I install Kubuntu without damaging Windows, while Windows will not start?

---

### Post by runningeagle on 2009-05-12
To be clear, this is about Kubuntu. I can't see how to edit the title to say [kubuntu]. If there is a way to install Ubuntu properly, I am certainly open to that.

---

### Post by mikewhatever on 2009-05-12
First about damaging Windows, since you want to install Kubuntu on a separate HDD, there is no danger of damage. To be on the safe side, you can even unplug the Windows HDD during the installation.

You should provide some more info to get better help:
What was wrong with Gparted? Any errors?
What are your pc specs?

---

### Post by tommcd on 2009-05-13
Herman's site has very good tutorials on dual booting Windows and Ubuntu:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Asiyu's site is very good as well:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by runningeagle on 2009-05-13
Hello and thank you for your quick reply,
 
Specs:
Windows XP x64 on C: drive, about 6 gigs of free space
Programs on D: drive, about 20 gigs free space.
Geforce fx 5200
3.00 ghz processor
 
Gparted started fine and when I went to partition the C: drive it quickly gave an error that gave no specific information (I assume it is because I had not defragmented the disk in a week, and I can't start XP to do so.)
 
So, I haven't done any partitioning and would like to put Kubuntu on the D: drive. I am at the install screen, but I am confused as to what to do to install just on the D: drive. I know I want it to be NTFS, but should I check the box marked format?
I'd rather not unplug the C: drive because I broke a previous computer trying to fiddle around in it. 
 
The Ubuntu live disk freezes on the desktop. There are some graphical glitches (several lines of red and green across the screen), the mouse moves and I can select icons but nothing happens, and the taskbars are missing. I decided to install Kubuntu because I thought Ubuntu was having problems, but is this an issue that is solved on a real install?

---

### Post by Mark Phelps on 2009-05-13
> **runningeagle said:**
> The Ubuntu live disk freezes on the desktop. There are some graphical glitches (several lines of red and green across the screen), the mouse moves and I can select icons but nothing happens, and the taskbars are missing. I decided to install Kubuntu because I thought Ubuntu was having problems, but is this an issue that is solved on a real install?
Generally speaking -- no.  There are exceptions like installing restricted drivers that improve the video, but if it doesn't work in the LiveCD, it generally won't work after install either.  Some things like Wireless can be relatively easy to fix.  Others, due to not detecting hardware, can range from difficult to impossible.

Also, would suggest you download and burn the GParted LiveCD from distrowatch and use that to partition the system, rather than attempt to do it as part of the install.

---

### Post by tommcd on 2009-05-13
The live CD should work with a nvidia 5200. I ran older versions of Ubuntu with a 5200 and it worked fine. After the install you could install the nvidia driver from the ubuntu repos which should fix the video problem.

When you boot up the Kubuntu CD, choose the option to "check disc for defects". If it fails, then burn a new disc. Be sure to burn the disc at the slowest possible speed.
Also, when you boot the live CD, try running it in safe graphics mode. If this still causes problems, then install using the 32 bit alternate install CD. This is a text based installer that will bypass the video problem.

When partitioning, choose manual partitioning. The 2nd hard drive will be /dev/sdb, and the first will be /dev/sda. Choose /dev/sdb and make 2 partitions, one for root and one for swap. The root partition will be formatted as ext3, not NTFS.

---

### Post by runningeagle on 2009-05-13
> **Mark Phelps said:**
> 
 
Also, would suggest you download and burn the GParted LiveCD from distrowatch and use that to partition the system, rather than attempt to do it as part of the install.
 
I tried using Gparted, but I got an error after clicking "resize/move". I assume it was due to not being able to Defrag before because XP will not boot.
 
TommCD:
 
In manual partitioning I have /dev/sda3 and /dev/sda5. I'm sorry if I am being overly cautious here, I have screwed up many times when using computers and I really don't want to do that this time. 
 
And is there a way I can use the livecd Kubuntu to place files that are non-essential but nice to have from my D: (non-windows) drive onto CDs/DVDs for backup? I would like to back up some game zip files and photos. I only have one CD drive, so can I mount the .iso somehow? Or is this not necessary because the partitioning will not delete anything?
 
Also, everytime, whether Ubuntu or Kubuntu, burned at 1x speed, MD5 is correct, using both Nero and Imgburn, both disks always come up as having 1 error in disk checking. 
 
I am sorry for asking so many questions. In the past, I have tried doing things using my best guess and it has not worked well on computers. 
 
Thanks!

---

### Post by tommcd on 2009-05-13
> **runningeagle said:**
> 
In manual partitioning I have /dev/sda3 and /dev/sda5.
If you have 2 hard drives they should be /dev/sda and /dev/sdb. The /dev/sda3 and /dev/sda5 refer to the 3rd and 5th partition on the 1st drive. 
Can you post the output of:
```
sudo fdisk -l
```
> **runningeagle said:**
>  
And is there a way I can use the livecd Kubuntu to place files that are non-essential but nice to have from my D: (non-windows) drive onto CDs/DVDs for backup? ... Or is this not necessary because the partitioning will not delete anything?
If you want to make backups you should do that from Windows before installing Kubuntu. 
The installer will only delete what you tell it to.
> **runningeagle said:**
>  
Also, everytime, whether Ubuntu or Kubuntu, burned at 1x speed, MD5 is correct, using both Nero and Imgburn, both disks always come up as having 1 error in disk checking. 
That should not happen. Does it report what file has the error? The md5sum check on the disc just checks the iso. The option to check the disc for defects checks every file on the CD against it's md5sum, so it is more thorough. Perhaps try using Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Or use different media.

---

### Post by runningeagle on 2009-05-13
I am assuming that is a lowercase l as in loud and not uppercase I as in Indiana.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf47e41ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3076       15017    95924115    f  W95 Ext'd (LBA)
/dev/sda2   *           1        3075    24699906    7  HPFS/NTFS
/dev/sda5            3076       15017    95924083+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 501 MB, 501219328 bytes
16 heads, 32 sectors/track, 1912 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1912      489456    e  W95 FAT16 (LBA)

It does not report the error file just "1 error found press enter to reboot". I have tried two different brands of DVDs and will now try using a CD and Infrarecorder. 

I have found all of my game install CDs and can back up photos to a USB stick, so I no longer need to save anything on the D: drive.

---

### Post by tommcd on 2009-05-14
Well fdisk correctly reports the 1st drive as /dev/sda and the 2nd drive as /dev/sdb. It reports /dev/sda as 123 GB. Is that correct?
Also, it is reporting /dev/sdb as only 501MB which can't be right. Did you have a 500MB flash drive plugged in to the computer when you ran fdisk?
How big is the 2nd hard drive? Is it an internal or external drive?

---

### Post by runningeagle on 2009-05-14
Ah, yes I did have a flash drive in. Here is the new one. 

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf47e41ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3076       15017    95924115    f  W95 Ext'd (LBA)
/dev/sda2   *           1        3075    24699906    7  HPFS/NTFS
/dev/sda5            3076       15017    95924083+   7  HPFS/NTFS

Partition table entries are not in disk order
ubuntu@ubuntu:~$



I burned both Ubuntu and Kubuntu to new CDs using Infrarecorder, but both still report 1 error found. I will try redownloading and try downloading 32-bit versions. Ubuntu gets to the desktop, but not functionality. 
I will try using alternate installer and safe graphics.

This is what I see in the installer:
[IMG]http://i21.photobucket.com/albums/b298/Runningeagle/snapshot1.jpg[/IMG]

---

### Post by tommcd on 2009-05-14
Fdisk and the Kubuntu partitioner are only seeing 1 hard drive. I'm not sure why that is. Fdisk finds 3 partitions on the drive. Kubuntu does not seem to see /dev/sda1
What is your setup? Are both these drives internal, or is the 2nd one external? Are they IDE or SATA? 

When you ran GParted, was it from the GParted live CD? Or was it from the Kubuntu live CD? I don't know why the 2nd drive is not being seen. If the 2nd hard drive is internal, perhaps you could try plugging it into a different SATA port (assuming it is a SATA drive). If they are IDE, set the jumpers for "master" and "slave" instead of "cable select". 

The only other thing I could suggest is trying to partition the 2nd hard drive with a Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)

---

