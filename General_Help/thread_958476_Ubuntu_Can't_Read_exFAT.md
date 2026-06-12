---
title: "Ubuntu Can't Read exFAT?"
date: 2008-10-25
forum: General Help
---

### Post by Killtodie on 2008-10-25
I just reformat my thumb drive from fat to exfat and now ubuntu doesnt detect it.

is there an issue with exfat on linux?

---

### Post by Killtodie on 2008-10-25
hmmm, yeah/ gparted sees it as unknown...


anyway to get it working?

---

### Post by cariboo on 2008-10-25
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=919423](http://ubuntuforums.org/showthread.php?t=919423)

especially post #2. There is no support for fatx in the stock kernel, you will have to modify the kernel to be able to access fatx.

Jim

---

### Post by zepotus on 2009-01-09
> **cariboo907 said:**
> Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=919423](http://ubuntuforums.org/showthread.php?t=919423)

especially post #2. There is no support for fatx in the stock kernel, you will have to modify the kernel to be able to access fatx.

Jim


Not FATx !!  It's exFAT.  Is there already support for exFAT?

---

### Post by XP1 on 2009-01-10
Linux is in trouble if there is no exFAT support.
 
All SDXC cards of 2009 use the exFAT file system.

---

### Post by gd6noob on 2009-01-12
hmm.. is this a new way for MS to put the killing blow to linux? knowing that more and more drives are just getting bigger in disk space??

will linux have support for this anytime soon?

---

### Post by Killtodie on 2009-01-17
Maybe 9.xx should have support. I dont see why this wont happen in the future. Not like its a licensing issue

---

### Post by adder1972 on 2009-01-30
Why is no exFat support a "killing blow to linux" ??? Ext4 is a superior and open file system.  We don't need exFat.

---

### Post by jerome1232 on 2009-01-30
Well there's a bug report on it

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/315710](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/315710)

But there doesn't seem to be a driver currently, found one mention of someone working on a read only driver for exfat (aka fat64).

[http://groups.google.com/group/linux.kernel/browse_thread/thread/312e5e6b9bf3c2b0/74664b574f8512fc?lnk=raot](http://groups.google.com/group/linux.kernel/browse_thread/thread/312e5e6b9bf3c2b0/74664b574f8512fc?lnk=raot)

I don't see how linux is in trouble, good read+write ntfs support is actually a fairly recent thing, I remember when I started using Linux about a year ago ntfs-3g wasn't considered stable. Just format your usb sticks back to fat32 and don't use fat64 until a driver comes out.

---

### Post by kumoshk on 2009-06-11
> **adder1972 said:**
> Why is no exFat support a "killing blow to linux" ??? Ext4 is a superior and open file system.  We don't need exFat.

I'm not going to say it's a killing blow to Linux, but it certainly would be annoying if we didn't get Linux support for it in the near future (as in the next year or two, if not long before). Why? Because SDXC cards (those that have just arrived to supplement SDHC) are catering to exFat, and that means that most portable devices are probably only going to support that file system&#8212;therefore, if we don't have Linux support, we can't use those devices without hacking them somehow.

Well, it's possible some will still support FAT32, but I doubt they all will. I'm sure with that kind of memory (up to 2TB), they'll come up with new kinds of devices to use it, and flaunt the cards on video cameras.

What are your thoughts?

Do you know of any portable media players that allow for an ext2 file system or such? That would certainly be nice. I wish the Cowon D2 did (that and have support for the Speex audio codec).

---

### Post by smit8678 on 2009-06-20
Here is a .deb for 9.04 using the 2.6.28-13 kernel. I compiled it from source and used checkinstall -D to make the .deb. It provides read-only capabilities. Anyone let me know when -rw capabilities are released.

---

### Post by kumoshk on 2009-06-20
Awesome! Thanks for that! Any chance it'll be included in apt-get some time in the future?

---

### Post by cprofitt on 2009-06-28
> **XP1 said:**
> Linux is in trouble if there is no exFAT support.
 
All SDXC cards of 2009 use the exFAT file system.

 ... format should work for that, heh?

---

### Post by kumoshk on 2009-06-30
> **cprofitt said:**
> ... format should work for that, heh?

Not exactly. Sure, it'll work if you're just using it for external storage, but if you try changing the file system for a card for something like an MP3 player, or a digital camera, you could have some major problems (and maybe not easily fixed, depending on a few things). Of course, not many use those cards yet, but I'm sure some day they will.

---

### Post by maximaximax on 2009-08-06
Ok, I installed the .deb package on my ubuntu 9.04. But how can I mount a volume with exFAT?

I tried:
$sudo mount -t exfat /dev/sdc1 /media/exfat

but it does not work:
mount: unknown filesystem type 'exfat'

Can somebody help me?

---

### Post by smit8678 on 2009-08-08
Hmm...interesting...I will look into it a little more. Did the .deb install okay? This may be a kernel issue that needs to be addressed in karmic. I will see what I can discover.

Something else for thought...MS made exFAT proprietary, so it may well be hard to find support. It might be best to reformat into vFAT (FAT16 or FAT32 depending on the size of flash drive).

***UPDATE***

From what I have been able to tell, any FAT64 support is experimental that this time and can get be buggy. The .deb that I posted is read-only. There are no -rw modules currently. If you used ubuntu only, formating in ext2/3 could work, but that would kill portability. There is a module for MS available that provides -rw support for ext2 available at [http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/) that would allow for portability in the same machine or other with the same patch, but it would make using it at public computers impossible. Let me know what you decide and I will keep searching...

---

### Post by maximaximax on 2009-08-09
.deb was installed okay in 9.04 (but it is jaunty, not koala - koala is 9.10).

My intention is to find a way of transfering large (>4GB) files from Windows to Linux. Of course there are several ext2 drivers for Windows, but Windows users looks suspiciious at them and don't like to install such drivers. From other hand these Windows users trust  Microsoft and allow to install exFAT drivers because they are from MS. So, if we at least can read exFAT in Linux it would be very useful - we can install exFAT on Windows and it will allow to transfer large files.

---

### Post by jerome1232 on 2009-08-09
Use ntfs? linux has r/w support for it and it supports >4gb files.

---

### Post by maximaximax on 2009-08-10
NTFS has a journal, which is not very good for flash memory - it writes too many times in one place and therefore reduces the USB-flash drive lifetime.

---

### Post by nosoupforyou on 2009-09-19
Hopefully this doesn't become too big of an issue but it appears licensing may be a problem [http://www.microsoft.com/iplicensing/productDetail.aspx?productTitle=exFAT%20File%20System%20Licensing%20Program](http://www.microsoft.com/iplicensing/productDetail.aspx?productTitle=exFAT%20File%20System%20Licensing%20Program)

If we are not allowed to distribute exFAT implementations for linux, then we won't be able to transfer any type of data between our pc and digital cameras, mp3s, etc. since re-formatting will be required, but then our device will not be able to use it and any data on it would be lost if you don't have a windows system to copy it over to first.

Maybe we can convince the SD association to use an open file-system such as JFFS2, NILFS, or one of the many other options designed for SSDs instead as the new standard.

---

### Post by ppirilla on 2009-09-19
> **nosoupforyou said:**
> Hopefully this doesn't become too big of an issue but it appears licensing may be a problem [http://www.microsoft.com/iplicensing/productDetail.aspx?productTitle=exFAT%20File%20System%20Licensing%20Program](http://www.microsoft.com/iplicensing/productDetail.aspx?productTitle=exFAT%20File%20System%20Licensing%20Program)

If we are not allowed to distribute exFAT implementations for linux, then we won't be able to transfer any type of data between our pc and digital cameras, mp3s, etc. since re-formatting will be required, but then our device will not be able to use it and any data on it would be lost if you don't have a windows system to copy it over to first.

Maybe we can convince the SD association to use an open file-system such as JFFS2, NILFS, or one of the many other options designed for SSDs instead as the new standard.

The linux community couldn't license the NTFS file sytem, either.  Eventually (and as was pointed out, very recently), someone was able to reverse-engineer a way to reliably read and write to that file system.

In the short term, we can get by with FAT32.  In the long term, I'm confident that someone in the FOSS community will come up with a working solution.

---

### Post by edwardtilbury on 2009-09-27
This does not look good, right now I'm setting up a laptop with windows 7 on the main partition and an extra partition of fatex so that later I can install dual boot 9.10 and share one partition between the two.  Windows 7 only formats to NTFS or exFAT, so I guess I should format it with NTFS instead of exFAT.

---

### Post by Tibor60 on 2009-10-21
It is why I think to return to windows. It is very good to advise to use NTFS, ext3, ext4 instead, but I can not reformat the usb sticks and memory cards what my friends give me to look at the photos. So, if we will not get the support, linux will be in trouble.

---

### Post by TheOnlyMrK on 2009-11-03
Has anyone gotten anything working on this? I've been looking everywhere for something that can make Ubuntu support exFAT, the only thing I've found sofar over the entire internet is the .deb made by "smit8678" but it doesn't work either because I'm on Ubuntu 9.10 not 9.04, or I just didn't know how to use it since no directions were given on its use, I assumed it would "just work". I've got a 8GB flash drive that's formatted in exFAT and is filled to the top with a backup of all my music and pictures that I need. Once I get my stuff off I'm going back to FAT32, this is the second thing I have that doesn't support exFAT, first is my PS3.

---

### Post by ericbarch on 2011-02-15
To anyone still looking for a solution to this, you can now mount exFAT drives as read/write fairly easily. Take a look at this link:

[http://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.html](http://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.html)

---

### Post by asmoore82 on 2011-02-15
must not give in &#8230;

too easy &#8230;

> **Tibor60 said:**
> &#8230; but I can not[*sic*] reformat the usb sticks and memory cards what my friends give me to look at the photos. So, if we will not get the support, linux will be in trouble.

There's this new thing called the "Enternet" -
apparently it's quite easy to view your friends' photos on that.

I think it even runs on Linux.

---

### Post by XP1 on 2011-02-15
> **asmoore82 said:**
> must not give in …

too easy …



There's this new thing called the "Enternet" -
apparently it's quite easy to view your friends' photos on that.

I think it even runs on Linux.How is that going to solve the problem when "my friends give me" an exFAT-formatted memory card?

When a friend takes out a memory card from his/her camera and immediately gives it to someone to look at the pictures, is that person going to reject the friend's offer and say, "Find your own exFAT-supported computer OS, upload the pictures online, and then return back to me."? How can you immediately view the pictures? You can't. Your workaround takes time.

---

### Post by Nabil Ali on 2011-02-22
exFAT FUSE Module for Ubuntu with Read/Write Support

[http://code.google.com/p/exfat/](http://code.google.com/p/exfat/)

sudo apt-get install subversion
sudo apt-get install scons
sudo apt-get install libfuse-dev
sudo apt-get install gcc
cd ~
svn co [http://exfat.googlecode.com/svn/trunk/](http://exfat.googlecode.com/svn/trunk/) exfat-read-only
cd exfat-read-only
scons
sudo scons install
cd ..
rm –rf exfat-read-only
sudo mkdir [mountpoint]
sudo mount –t exfat-fuse [device_path] [mountpoint]

TESTED AND WORKING ON UBUNTU 10.10 :popcorn:

---

### Post by Kaliree on 2011-03-01
So I am nearly illiterate in the use of Terminal. I'm working on it. :( Anyhow, I followed Nabil Ali's directions. Everything seems to have worked correctly (no error messages of any kind), except for the mount. I still can't see my exFAT hard drive under "Places" in the GUI. I do see it listed as a device the Disk Utility, but it doesn't recognize the format of the partitions. 

I tried to mount the device following Nabil's instructions, but nothing mounts (as far as I can tell). I don't know the command to list "mounted devices" though. 

So, what is the command to list all mounted devices and is there a way to mount my exFAT external hard drive? I have it running over USB 2.0 right now, but I would also like to try to get this working over eSATA. Any suggestions? [-o<

---

### Post by jerome1232 on 2011-03-02
Just type mount with no parameters and you'll get a list of all mounted filesystems.

---

### Post by Clayton7510 on 2011-07-28
> **Kaliree said:**
> So I am nearly illiterate in the use of Terminal. I'm working on it. :( Anyhow, I followed Nabil Ali's directions. Everything seems to have worked correctly (no error messages of any kind), except for the mount. I still can't see my exFAT hard drive under "Places" in the GUI. I do see it listed as a device the Disk Utility, but it doesn't recognize the format of the partitions. 

I tried to mount the device following Nabil's instructions, but nothing mounts (as far as I can tell). I don't know the command to list "mounted devices" though. 

So, what is the command to list all mounted devices and is there a way to mount my exFAT external hard drive? I have it running over USB 2.0 right now, but I would also like to try to get this working over eSATA. Any suggestions? [-o<
If you struggle with the command line then it might be easier for you to simply put the mount command in a script (.sh file).  Unfortunately, exFat will not auto-mount in Linux.  But it's really not too hard to mount an exFat drive.  If you are still confused by Nabil Ali's instructions then check out my blog post on this subject: [http://claytonlong.blogspot.com/2011/07/exfat-fat64.html](http://claytonlong.blogspot.com/2011/07/exfat-fat64.html). It walks you through every step and explains why each command is used.

---

### Post by masuch on 2011-09-18
> **Nabil Ali said:**
> exFAT FUSE Module for Ubuntu with Read/Write Support

[http://code.google.com/p/exfat/](http://code.google.com/p/exfat/)

sudo apt-get install subversion
sudo apt-get install scons
sudo apt-get install libfuse-dev
sudo apt-get install gcc
cd ~
svn co [http://exfat.googlecode.com/svn/trunk/](http://exfat.googlecode.com/svn/trunk/) exfat-read-only
cd exfat-read-only
scons
sudo scons install
cd ..
rm –rf exfat-read-only
sudo mkdir [mountpoint]
sudo mount –t exfat-fuse [device_path] [mountpoint]

TESTED AND WORKING ON UBUNTU 10.10 :popcorn:

thanks for info, +1.

---

### Post by draugruin on 2011-09-26
Thanks Nabli! Confirmed it works for Ubuntu 11.03.

---

### Post by win2456 on 2011-10-23
> **Nabil Ali said:**
> exFAT FUSE Module for Ubuntu with Read/Write Support

[http://code.google.com/p/exfat/](http://code.google.com/p/exfat/)

sudo apt-get install subversion
sudo apt-get install scons
sudo apt-get install libfuse-dev
sudo apt-get install gcc
cd ~
svn co [http://exfat.googlecode.com/svn/trunk/](http://exfat.googlecode.com/svn/trunk/) exfat-read-only
cd exfat-read-only
scons
sudo scons install
cd ..
rm –rf exfat-read-only
sudo mkdir [mountpoint]
sudo mount –t exfat-fuse [device_path] [mountpoint]

TESTED AND WORKING ON UBUNTU 10.10 :popcorn:

Thanks Nabil, worked like a charm!  I'm on Ubuntu 11.10...

---

### Post by bvanaerde on 2012-02-15
Thanks for this post... I was searching for a way to get the files from my JVC Everio GZ-HM445. After installation, it's not needed to mount the camera, as Ubuntu does this by itself.

---

### Post by bvanaerde on 2012-07-02
Tested and working on Ubuntu 12.04 64bit

---

