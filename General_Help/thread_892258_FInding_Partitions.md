---
title: "FInding Partitions"
date: 2008-08-17
forum: General Help
---

### Post by Ribosome on 2008-08-17
Hello everyone, just want to say that I'm a beginner and really liking Ubuntu at the moment.  I've read a lot of posts and google'd some stuff, but I barely have scratched the surface.  I'm looking forward to getting to know it better.

Anyway, enough of that.  My issue that I have right now is that I *thought* I had partititioned my hard drive correctly, but that does not seem to be the case considering grub doesn't pick up Vista at the startup menu.

I have tried to edit the /boot/grub/menu.lst with root (hd0,0), and I get the error message "Error 13:Invalid Device Recognized".  Same thing happens when I put (hd0,1).

Now, I'm not sure if this is possible, but could Ubuntu have overwritten Vista?  If that is the case, is there anyway to check what partitions there are- if any a all?

But, the thing is when I go Applications->Accessories->Disk Usage the filesystem usage is set at 5.5gb, the amount of the separate partion created for Ubuntu.  This gives me the notion that maybe Vista is still on the hard drive, just being pushed aside.

If Vista has been overwritten, that is fine.  I don't necessarily need anything on it.  There is just one file on it that I forgot to back up.  So if a clean install of Vista is in order, then so be it but I'd like to be able to get to it cleanly.

Thanks in advance.  If this is in the wrong place, then please move it and I apologize in advance.

---

### Post by Yuki_Nagato on 2008-08-17
Sure.  Ubuntu could have easily overwritten Vista.  But to be sure, we need disk partitioning software.

There should be some on the Ubuntu install software.

Boot up the LiveCD if you have it, and then go the System>Administration>Disk Partitioning.

We will be looking for a NTFS partition.  If it is still there, memorize the number, and enter that into the menu.lst file.

If there is no NTFS partition, Vista was overwritten.

New Technology File System - Windows
ext2 (old), ext3 (current), ext4 (Fedora is experimenting with it) - Linux

---

### Post by ibutho on 2008-08-17
Hi,

Run Applications -> Accessories -> Terminal and enter
```
sudo fdisk -l
```
Post back the output.

---

### Post by Ribosome on 2008-08-17
ibutho, this is what I came up with:

[PHP]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb21d0910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19070     2971993+  82  Linux swap / Solaris
/dev/sda6           19071       19433     2915766   83  Linux
/dev/sda7           19434       19457      192748+  82  Linux swap / Solaris
[/PHP]

Yuki, I'm going to try what you said right now and edit.

Edit:  I could not find System->Administration->Disk Partitioning.  The CD I'm using is a burned ISO image I downloaded off of Ubuntu's website.  I'm not sure if that and LiveCD would be the same thing.

---

### Post by ibutho on 2008-08-17
From the output, you do not have any ntfs or fat32 partitions, which means that Windows was wiped off when you installed Linux. I guess you accidentally selected the option to use all of the disk for Ubuntu.

---

### Post by Ribosome on 2008-08-17
Ah, well.

So, now that I don't need partitions, how could I make Ubuntu use the entire hard drive?  The disk usage says I'm using 5.5gb (which is 70% full) so there is 154.5gb not being used.  Or does that not really matter?

Thanks for the fast replies :)

---

### Post by ingeva on 2008-08-17
> **Ribosome said:**
> how could I make Ubuntu use the entire hard drive?  The disk usage says I'm using 5.5gb (which is 70% full) so there is 154.5gb not being used.  Or does that not really matter?


You have two swap partitions, and one of them is rather large.
You might use a LiveCD, run "gksudo gparted" and remove the largest one.
The easiest way to fix everything might actually be to remove all partitions, and then re-install from scratch. With only one hard disk let the install make the partitions for you automatically and you'll get an optimal use of your disk.

If you have changed many settings, try to backup at least your home directory before you go.... :)

---

### Post by Ribosome on 2008-08-17
> **ingeva said:**
> You have two swap partitions, and one of them is rather large.
You might use a LiveCD, run "gksudo gparted" and remove the largest one.
The easiest way to fix everything might actually be to remove all partitions, and then re-install from scratch. With only one hard disk let the install make the partitions for you automatically and you'll get an optimal use of your disk.

If you have changed many settings, try to backup at least your home directory before you go.... :)

Okay I did what you told me and the screenshot below is what I got.

Now, I would just delete all of them, however there is one rather big partition that looks like it could be Vista.  Although it is damaged.  Which ones should I delete? All of them and then install from this CD?  Just want to make sure I don't screw up any further ;)

Also, I was going to wait to customize until I got everything figured out, at least I did something right :)

---

### Post by az on 2008-08-17
Yup, it looks like your Vista could still be there.

The partition type is Linux, but you can change that back to NTFS.  You can also see if you can mount it.

In a terminal try

mkdir vista
sudo mount /dev/sda1 vista

Depending on the error you get, you may be able to use some tools to fix the NTFS filesystem.

---

### Post by Ribosome on 2008-08-17
```
mount: you must specify the filesystem type

```

Thats what I get.  When I replace Vista with Windows, it tells me that the "mount point windows does not exist".

Do you think it is worth it to try and find NTFS tools, or just erase it and start over.  I have no problem with losing Vista if it's going to be a pain to get it back.

---

### Post by az on 2008-08-17
If it works, it shouldn't be too painful.  

In the commands I gave you, "vista" was the name of the directory you created to mount the partition. It doesn't matter what you call it.

Try mounting it like this:

sudo mount -t ntfs /dev/sda1 vista


Regardless of what it says, I would suggest you install ntfsprogs and run

sudo ntfsfix /dev/sda1

and try again.

You can also try repairing the boot sector:

[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)

If you can finaly mount the filesystem, then you can change the partition type back to NTFS and it should work fine for you.

If you can't mount the partition with the two suggestions above, I would give up and delete the partition and put the space back to use, as you suggest.  You could do that with any partition tool.

---

### Post by Ribosome on 2008-08-17
Okay, I may have fixed the NTFS partition.  I was able to install ntfsfix and then in Disk Partition Editor I right clicked the first partition that was "unknown" and formatted it to NTFS.

Now, I re-ran ```
sudo fdisk -l
``` and came up with

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb21d0910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+   7  HPFS/NTFS
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19070     2971993+  82  Linux swap / Solaris
/dev/sda6           19071       19433     2915766   83  Linux
/dev/sda7           19434       19457      192748+  82  Linux swap / Solaris


So it appears that vista is still there.  I'm going to try and edit the grub so that it will be an option when booting up (currently it gives an Error 12: Invalid Device Recognized).  But I think I know how to fix that (put my /boot/grub/menu.lst for vista back to (hd0,0).  I'll post back if I can't.

Thanks for the advice so far, I really appreciate it :)

Edit:  When I try to get into vista now, it says that "BOOTMGR is missing" and makes me restart.  Any suggestions on how to get around that?

Edit2: It seems the only way to fix the missing BOOTMGR is to use the Vista recovery CD.  I have my Laptop Recovery, which came with my this computer but it only allows me to reformat, and not "Repair".  Reformatting would erase everything (I assume anyway) Ubuntu included.  I suppose this isn't a bad option, as it allows me to install Windows on one partition and leave another blank.  I might do this option.

---

### Post by az on 2008-08-17
> **Ribosome said:**
> Okay, I may have fixed the NTFS partition.  I was able to install ntfsfix and then in Disk Partition Editor I right clicked the first partition that was "unknown" and formatted it to NTFS.


What did ntfsfix say when you ran it?  Were you able to mount the partition afterwards?

Also, I hope you didn't format the partition.  What I said was to change the partition type to NTFS - that's not formatting.  Formatting erases the filesystem.  Changing the partition type only affects the partition table.

---

### Post by ingeva on 2008-08-17
> **Ribosome said:**
> ... Disk Partition Editor I right clicked the first partition that was "unknown" and formatted it to NTFS.


Yeah, if you really did that, you deleted everything in the partition. If you have a backup of your files, fine. Otherwise they are lost and you would need very advanced tools to find the contents again. You can't do that yourself, and it's very expensive; probably more than a new computer.

---

### Post by Ribosome on 2008-08-17
> **az said:**
> What did ntfsfix say when you ran it?  Were you able to mount the partition afterwards?

Also, I hope you didn't format the partition.  What I said was to change the partition type to NTFS - that's not formatting.  Formatting erases the filesystem.  Changing the partition type only affects the partition table.

Ahh shoot.  I guess I did erase the drive while formatting by accident.  It now says in the Partition Editor the drive is 143.25gb and only using 90mb.

I was able to mount the drive, however nothing is in the folder now that everything seems to have been deleted (d'oh).

Anyway, I think what I'm going to do is delete **all** the partitions and boot the recovery CD for Vista with two partitions.  Then install Ubuntu on the other partition.

Well it seems like Vista was there until I formatted it away!

Thanks for all the help, I appreciate it :)

---

### Post by az on 2008-08-17
> **ingeva said:**
> Yeah, if you really did that, you deleted everything in the partition. If you have a backup of your files, fine. Otherwise they are lost and you would need very advanced tools to find the contents again. You can't do that yourself, and it's very expensive; probably more than a new computer.

You actually can recover files that way.  It's called file-carving.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

### Post by ingeva on 2008-08-18
> **az said:**
> You actually can recover files that way.  It's called file-carving.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

You can recover deleted files, but you can't recover files from a formatted partition that way, because the files are overwritten.
If Quick Format was used, however, you might have a chance.

To recover from a formatted disk, the disk must be taken apart and analog investigation tools must be used to recover the magnetic traces from before the format operation.

---

### Post by az on 2008-08-18
> **ingeva said:**
> You can recover deleted files, but you can't recover files from a formatted partition that way, because the files are overwritten.
If Quick Format was used, however, you might have a chance.

To recover from a formatted disk, the disk must be taken apart and analog investigation tools must be used to recover the magnetic traces from before the format operation.

Even a "long format" leaves the data behind.  It performs a read-only test and overwrites the filesystem data, but the raw data from most of the files is still there.

So, to make the data from a drive unrecoverable by software, the drive either needs to be physically damaged or someone needs to purposefully write to every block - and you can't do that by accident using Windows.

---

### Post by ingeva on 2008-08-18
> **az said:**
> Even a "long format" leaves the data behind.  It performs a read-only test and overwrites the filesystem data, but the raw data from most of the files is still there.

So, to make the data from a drive unrecoverable by software, the drive either needs to be physically damaged or someone needs to purposefully write to every block - and you can't do that by accident using Windows.

Then it's very strange that the links you refer to don't mention a word about recovering data from formatted disks. I've worked with computers for many years, and everything I've heard and read tells me you need special tools to do that.

Even if you could recover bits of data by reading sector by sector, there's also the question of organizing that data, connecting the bits together and rebuild a usable directory structure.

Luckily, in my nearly 40 years of working with computers, the question has only been theoretical. Never needed anything like it in practice. After all, there's something called backup. :)

---

### Post by az on 2008-08-18
> **ingeva said:**
> Then it's very strange that the links you refer to don't mention a word about recovering data from formatted disks. I've worked with computers for many years, and everything I've heard and read tells me you need special tools to do that.

The first paragraph of the DataRecovery wiki page reads:

"Deleted or lost files can usually be recovered from failed or formatted drives and partitions, CD-ROMs and memory cards using the free/libre software available in the Ubuntu repositories."

> **ingeva said:**
> 
Even if you could recover bits of data by reading sector by sector, there's also the question of organizing that data, connecting the bits together and rebuild a usable directory structure.

[http://en.wikipedia.org/wiki/Data_recovery#Data_carving](http://en.wikipedia.org/wiki/Data_recovery#Data_carving)

I have not found any proprietary software that does a better job at file carving than Photorec and Foremost.

> **ingeva said:**
> 
Luckily, in my nearly 40 years of working with computers, the question has only been theoretical. Never needed anything like it in practice. After all, there's something called backup. :)

I do this professionally.  I do not charge unless I recover a significant amount of data.  I have yet to not recover a significant amount of data from a formatted drive - and usually, the client has reinstalled windows over the drive.  Since drives are so large these days, there still remains a large amount of important data (like family photos) on the drive.

---

### Post by ingeva on 2008-08-18
> **az said:**
> "Deleted or lost files can usually be recovered from failed or formatted drives and partitions, CD-ROMs and memory cards using the free/libre software available in the Ubuntu repositories."

OK, I missed that.
However, it also sais:

> Also, data carving requires that the files recovered be located in sequential sectors (rather than fragmented) as there is no allocation information to point to fragmented file portions. This method can be time and resource intensive.


So it's not easy, and very prone to errors.
I've seen how fragmentet many folks's hard drives are. Only using Windows, they generally have no idea about defragmenting.

However, you evidently know more about this than I do, and probably make a lot of money saving files for customers, so I'll be wise enough to not object any more! :)

---

### Post by ingeva on 2008-08-18
> **az said:**
> 
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)


I tried to download that program. Failed three times.
This has not happened before. I want to check whether your statements are true, and I have a used disk lying here, with an NTFS partition converted to ext3 and reformatted.

I'm still very skeptical, and want to see before I believe. I'll try a new download tomorrow. Maybe the conditions are better then.

---

