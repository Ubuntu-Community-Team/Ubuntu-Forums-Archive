---
title: "NTFS corrupted by Ubuntu writing"
date: 2010-05-31
forum: Hardware
---

### Post by Zortrox on 2010-05-31
I have Ubuntu 10.04 installed on my laptop (ASUS-UX50v) and when I mount and write files to my NTFS partition (like copying videos and music over so Windows will be able to read them) the files become unreadable.  Also, when I start some programs a notification comes up saying that the file is corrupted.  I run chkdsk in Windows and everything is back to normal, but the files I copy over are deleted.

What is the problem?  Is there a way that I can copy files to a NTFS partition without the file system being corrupted or does Ubuntu have problems with that in general?  Thanks in advance!

---

### Post by Zortrox on 2010-06-18
I still have this problem.  The space on my ext3 partition is slowly dwindling.  Any help would be appreciated.  Thanks!

---

### Post by wilee-nilee on 2010-06-18
You have given no detail how can we help you. What type of files what type of anything be specific and detailed. And have you checked your Hd for errors and broken areas?

I would also run a test take a copy of any file or whatever put it on a thumb or dvd and put one copy in the ntfs partition then the copy straight into MS from the media and see if the same thing happens.

---

### Post by darolu on 2010-06-18
Posting the result of the following commands will help to diagnose (you can copy-paste in your terminal):
```
sudo fdisk -l
```
```
cat /etc/fstab
```
Also try to be more specific; list what steps you follow (i.e. how do you mount your ntfs partition), what do you expect to happen and what happens instead.

---

### Post by gsk on 2010-06-18
Sir,

On a second look it appears I am putting my request out of place. But I will take a chance. 

I had been looking for help in booting up my Presario V3100 in Win XP SP2, which was working normally but by mistake I reset the bios to default setting. Thereafter it would showup the intial Compaq screen gives an option of safe boot etc and brief flash of Windows loading and then automatically going in for reboot. 

Could it be a MBR problem or some thing else. I have some data which I had not backed up.

I will be grateful for a reply.
 
Thanks
 
GSK

---

### Post by wilee-nilee on 2010-06-18
> **gsk said:**
> Sir,

On a second look it appears I am putting my request out of place. But I will take a chance. 

I had been looking for help in booting up my Presario V3100 in Win XP SP2, which was working normally but by mistake I reset the bios to default setting. Thereafter it would showup the intial Compaq screen gives an option of safe boot etc and brief flash of Windows loading and then automatically going in for reboot. 

Could it be a MBR problem or some thing else. I have some data which I had not backed up.

I will be grateful for a reply.
 
Thanks
 
GSK

First start your own thread.;)

---

### Post by Zortrox on 2010-06-18
"sudo fdisk -l" gives me:[INDENT]```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003656f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       41199   330930936    7  HPFS/NTFS
/dev/sda2           53617       60215    53000193    5  Extended
/dev/sda3   *       47727       53616    47311425    7  HPFS/NTFS
/dev/sda5           53617       59841    49999872   83  Linux
/dev/sda6           59841       60215     2999296   82  Linux swap / Solaris
```[/INDENT]and "cat /etc/fstab" gives:[INDENT]```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=fbafad06-aa5f-404f-8688-70b557e4bcb5 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7e662513-ed6c-4351-80df-b9324122ffc7 none            swap    sw              0       0
```[/INDENT]I mount the NTFS device by just double clicking it in nautilus.  The drive I'm copying it to (sda1) is my central media drive where I store my music and movies.  I just copy/pasted an mp3 file that I downloaded into my song directory on the drive to load up into iTunes, but when I booted into Windows 7 and tried to play the song (even with VLC), it wouldn't play.  I had copied it to my flash drive (FAT32) and then was able to play it in Windows.

If any more information is needed, I will gladly supply it.  Thanks for the help too.  I'm fairly new at Linux and the forums.

---

### Post by darolu on 2010-06-18
I think you may not be getting the right permissions to write files in your NTFS partition when mounting; you can give the right permissions via fstab file, in order to do it you need to create a mountpoint for your device first, simply create a directory within /media/ (so it's automatically listed in your Nautilus list/places panel):
```
sudo mkdir /media/<mydrive>
```
Substitute "<mydrive>" with whatever you want. After creating the directory (mountpoint) edit your fstab file with your favourite text-editor; super user powers will be needed (sudo):
```
gksudo gedit /etc/fstab
```
Add these lines at the end of the file and save:
```
# NTFS partition /dev/sda1
/dev/sda1 /media/<mydrive>            ntfs    defaults,user,exec,rw              0       0
```
Again, remember to replace "<mydrive>" with whatever you have chosen; after saving your file run this in your terminal to mount it:
```
sudo mount -a
```
The set of options (defaults,user,exec,rw) should let you write, read and execute anything from/to your NTFS partition; copy your mp3 file from the terminal to check if there are other problems:
```
$ cd your/directory/
your/directory$ cp yourfile.xxx /media/<mydrive>/
```

=== OPTIONAL (recommended) ===
It is recommended to use UUID (Universally Unique Identifier) code instead of your /dev value in your fstab file, just like the Ubuntu installer did for your / and swap partitions; to find out what is the UUID for your /dev/sda1 partition run:
```
blkid -o full -s UUID
```
Copy the code that corresponds to your /dev/sda1 partition and edit your fstab file:
```
gksudo gedit /etc/fstab
```
Replace /dev/sda1 with the UUID value you copied from blkid, don't forget to remove the quotation marks:
```
UUID=400AA41B7790B28A /media/<mydrive>            ntfs    defaults,user,exec,rw              0       0
```

---

### Post by Zortrox on 2010-06-19
It worked perfectly!  Thank you so much for all of your help.  One final question though:  Do I always have to mount it by using the command "sudo mount -a" or can I just double click on the drive in nautilus and add/remove files as needed?  Thanks!

---

### Post by think13 on 2010-06-19
> **Zortrox said:**
> It worked perfectly!  Thank you so much for all of your help.  One final question though:  Do I always have to mount it by using the command "sudo mount -a" or can I just double click on the drive in nautilus?  Thanks!

Since you added that entry to fstab, it should be mounted at boot time, so you shouldn't have to manually mount it any more.

---

### Post by Zortrox on 2010-06-19
Thanks!  This makes me ask another question though...  Can I set my Rhythmbox library on that partition without having to manually mount it?  And can I add entries to fstab for all of my partitions so I don't have to manually mount them when I log in?  Thanks!

---

### Post by darolu on 2010-06-19
Yes, you can use it for your Rhythmbox library as it auto-mounts at boot (I use a secondary hard drive for my music/videos and works great); and yes you can add all of your partitions.

---

