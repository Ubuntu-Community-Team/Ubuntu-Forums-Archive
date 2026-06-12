---
title: "Unable to mount location,  Can't mount file"
date: 2009-02-18
forum: Hardware
---

### Post by houseonfire on 2009-02-18
I've searched around but cant seem to find a solution to my problem.
This drive used to run under linux (about 7 months ago it did) and now it doesn't want to mount for me. 
Can someone help me out please?


[IMG]http://img24.imageshack.us/img24/5576/screenshotcomputerfileboh1.png[/IMG]


[IMG]http://img8.imageshack.us/img8/6774/screenshoterrorwindowxj0.png[/IMG]


[IMG]http://img23.imageshack.us/img23/3339/screenshotusbdrivepropeys1.png[/IMG]


It's imperative that the information on this drive is not deleted. But if i can get this mounted by formatting it, how can I recover the information?

---

### Post by houseonfire on 2009-02-18
I'm bumping this thread because I really need help.

---

### Post by houseonfire on 2009-02-18
He guys. I'm still looking for some help on this issure.
Thanks

---

### Post by houseonfire on 2009-02-18
This can't be that hard of a question to answer.
I'm just slightly new to linux

---

### Post by geraldm on 2009-02-18
I do not know for sure, but I was thinking that your system may be set up to mount the drive in (example:) /mnt/toofar and there is no longer a directory "toofar" and so it cannot mount THAT location.  Use the command "ls -d " followed by the place you are trying to mount it.

read the man page for "mount", and if you cannot figure it out, then post the command that you are using to try to mount 

Gerald

---

### Post by houseonfire on 2009-02-19
```
tim@tim-desktop:~$ sudo fdisk  /media/sda2
last_lba(): I don't know how to handle files with mode 40755
You will not be able to write the partition table.

Unable to read /media/sda2
tim@tim-desktop:~$ 

```

I get that when i run fdisk to the drive. 
The path exists (i think) it just wont mount.

---

### Post by houseonfire on 2009-02-19
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c5d0c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 159.8 GB, 159840301056 bytes
26 heads, 50 sectors/track, 30018 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30019   156093788    b  W95 FAT32

```

My main drive is 500gb
The drive I want to get working is 250 gb.
I have a 160gb iPod plugged in, and a DVD Drive.
When i tried to get the 250gb drive to work in windows, it said I had a i/o error.

---

### Post by houseonfire on 2009-02-19
bumping. i need this info please.

---

### Post by houseonfire on 2009-02-19
bump

---

### Post by geraldm on 2009-02-19
Just try to mount the disk.  Since it used to work in linux, then the filesystem type
was also available for that linux version.
try:
sudo mount -t auto /dev/sda2 /media/sda2
To find out the filesystems available on your system:
cat /proc/filesystems
After you figure out how to mount the disk, copy off the files you want to save. 
Use a command like fdisk only if you know what you are doing, and are really careful.

Gerald

---

### Post by houseonfire on 2009-02-19
I've tried to mount it.
I'm unsure how to use those commands you posted.
This drive might be corrupted. How can I access the data so i can copy it over? Any handy tools out there for advanced file recovery?

---

### Post by houseonfire on 2009-02-20
bumping

---

### Post by houseonfire on 2009-02-21
-.-
bumping.

---

### Post by houseonfire on 2009-02-24
Can someone please help me?

---

### Post by houseonfire on 2009-02-25
I'm gonna go ahead and bump this thread.

---

### Post by houseonfire on 2009-02-26
b..u...m..p

---

### Post by houseonfire on 2009-02-27
b u m p

---

### Post by houseonfire on 2009-02-27
Today it actually got as far as saying "250GB Media" So I know it can be read.

I tried MountPy -m in the console, and it just sits there and scans the drive. Makes the drive really hot and doesn't do anything.
I also tried photorec but it neveris able to read the drive, just like mountpy.

---

### Post by vanadium on 2009-02-27
I am afraid your 250 GB drive did not show up in the output of "sudo fdisk -l" that you showed. First, try again: remove all USB devices except the drive, make sure it is powered on. Then run the command

```

sudo fdisk -l

```

and post the output here.

Do also post the output of the kerne log: maybe that will also help.

```

dmesg | tail -n 30

```

If it does not show up, you have to suspect a hardware error (USB port, USB cable, hard drive, ...). If it does, I can give the command to mount it. If the problem is in the mounting, the output of the command will tell the reason so we will know what to try next.

---

### Post by houseonfire on 2009-02-27
I ran the fdisk thing and it just freezes half way through. I assume when it hits the 250gb drive.

---

### Post by vanadium on 2009-02-27
Looks like the data are gone.

---

### Post by houseonfire on 2009-02-28
The data is never completely gone.
It is possible to get the data back if I can get some help with recovering it.

You are wrong vanadium.

---

### Post by vanadium on 2009-02-28
> You are wrong vanadium.
Unfortunately, I might be right, although I have to admit that data rescue can go a long way if you are prepared to pay thousands of dollars to a specialized company.

The symptoms you describe indicate problematic hardware to me. Not a major problem normally if you have a backup of your data. If you don't, then indeed you will want to do any effort to try to rescue the data.

You simply cannot access the data with your current operating system and your current computer. It simply cannot correctly recognize the hardware, leave alone recognising and mounting file systems on it. Try to access the data from a live CD. Try to access the data from a live CD of another linux distro. Take the drive to another computer, see what results you get there. As long as you do not get the drive properly listed in "sudo fdisk -l" you have a big problem.

A way to reveal symptoms would be to plug in the drive, then look at the output of "dmesg". This indicates how the kernel reacts when it sees you have connected the drive. Post the last 30 lines or so here, so people more experienced than me might perhaps be able to give you a possible approach.

```

dmesg | tail -n 30

```

---

### Post by Russell Burrows on 2009-02-28
> **houseonfire said:**
> The data is never completely gone.
It is possible to get the data back if I can get some help with recovering it.

You are wrong vanadium.

Did you try mount manager

Turn your computer off, then unplug the USB cable and then the power to the drive. Restart you computer, plug the power into the hard drive, wait 10 seconds and then plug the USB into the computer. This clears the hard drive buffer. See if the drive shows up in disk management.

I noticed that if a corrupt usb drive or external mouse fails to mount on my Ubuntu laptop or work then in my case I fireup Virtualbox and try to mount/recognize equipment from there and if that fails then I run a data recovery program from inside virtual xp like active file recovery pro

wait, wait also in virtualbox xp I sometimes have sucess with clone cd mounting a corrupt usb drive as a cd image and I have no idea why clone cd tries to mount the usb drive as a cd drive


Or
Try this

[http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml)


 	
Linux Recovery Software
	

R-Linux is a free file recovery utility for the Ext2FS/Ext3FS file system used in the Linux OS and several Unixes. R-Linux uses InteligentScan technology and flexible parameter settings that give you real control over the fastest data recovery ever seen. It recovers files from existing logical disks even when file records are lost. However, there is no any network capabilities or ability to reconstruct damaged RAIDs or stripe sets in R-Linux.
Download Now

R-Linux recover files 	

    * Removed by virus attack, power failure or system crash;
    * After the partition with the files was reformatted, even for different file system;
    * When the partition structure on a disk was changed or damaged. In this case, R-Linux can scan the disk trying to find previously existed partitions and restore files from found partitions.
    * From disks with bad sectors. In this case, R-Linux can first copy the entire disk or its part into an image file and then process such image file. This is especially useful when new bad sectors are constantly appearing on the disk, and remaining information must be immediately saved.
    * Recovers files on damaged or deleted partitions.


New R-Linux features in version 3.x 	

    * Support for known file types. R-Linux searches for files with known typical features of their structures allowing the user to search for files on devices with unknown files systems, including an HD, CD, DVD, floppy disk, Compact Flash Card, USB drive, ZIP drive, Memory Sticks, and other removable media.
    * Scan process visualization. While scanning an object, R-Linux graphically shows items that have been found.
    * A hexadecimal disk and file editor.
    * Patterns (or templates) in the hexadecimal editor allowing for parsing the data according to specific data structure. Such patterns may be custom-created.
    * GPT and APM partition layout schema support.


R-Linux features 	

    * Standard "Windows Explorer" - style interface.
    * Host OS: Win9x, ME, NT, 2000, XP, 2003, Vista.
    * Supported file systems: Ext2FS/Ext3FS (Linux) only.
    * Recognition and parsing Dynamic (Windows 2000/XP/Vista), Basic, GPT and BSD (UNIX) partitions layout schema and Apple partition map. Dynamic partitions over GPT are supported as well as dynamic partitions over MBR.
    * Creates image files for an entire hard drive, logical disk, or its part. Such image files can be processed like regular disks. Images can be either simple exact object copies (Plain images) compatible with the previous versions of R-Linux, or compressed images that can be compressed, split into several parts, and password-protected. Such images are fully compatible with the images created by R-Drive Image, but incompatible with the previous versions of R-Linux.
    * Recognizes localized names.
    * Recovered files can be saved on any (including network) disks accessible by the host operating system.

---

