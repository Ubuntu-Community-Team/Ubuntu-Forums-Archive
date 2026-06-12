---
title: "Cant't mount broken Windows HDD which is GPT"
date: 2015-08-25
forum: Hardware
---

### Post by Jefferson1 on 2015-08-25
Hello,

i want to rescue a friends data from a broken Windows 8 by using a Ubuntu live-CD. Problem is, that I can't mount the HDD and I don't know what to do since the HDD is GPT, so [this method ]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/")doesn't work for me. 

Any advice? Thank you

Edit

this ist the output of fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb90ac906

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

-----------------------------------------------------------------------------------------


i can mount /dev/sda1, which is the recovery partition.

---

### Post by weatherman2 on 2015-08-25
Supported versions of Ubuntu can read Windows GPT hard drives.  Try typing this command in a terminal (Ctrl Alt t opens a terminal):

```
sudo parted -l
```

(or start the program Gparted to see the graphical version.)

Do you see any partitions?

How do you know the hard drive hasn't failed?  You can check the drive's S.M.A.R.T. health and Attributes with GSmartControl which you would have to install in Ubuntu - enable the "Universe" repository in Software Center first and have an internet connection.  You could also try the Linux distro called Parted Magic.  There is a free version of that (now a couple of years old) available at Major Geeks.  it has GSmartControl already installed, called "Disk Health."

---

### Post by Jefferson1 on 2015-08-25
this is the output of pared -l

> root@ubuntu:~# parted -l
Error: Input/output error during read on /dev/sda                         
Retry/Ignore/Cancel? i                                                    
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs         Basic data partition          hidden, diag
 2      1050MB  1322MB  273MB   fat32        EFI system partition          boot, hidden
 3      1322MB  2371MB  1049MB  fat32        Basic data partition          hidden
 4      2371MB  2505MB  134MB                Microsoft reserved partition  msftres
 5      2505MB  451GB   449GB   ntfs         Basic data partition
 6      451GB   452GB   472MB   ntfs                                       hidden, diag
 7      452GB   479GB   26.8GB  ntfs         Basic data partition
 8      479GB   500GB   21.5GB  ntfs         Basic data partition          hidden, diag


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

I also edited the output of fdisk -l in the start-post.

Trying to get the Universe repository gives me the error-message that it can't install due to a missing internet-connection although i have acces to the internet.

edit: /dev/sda5 seems to be the main-partition, right? i tried mounting it, getting the following message:

> root@ubuntu:~# sudo mount /dev/sda5 '/home/ubuntu/Desktop/lol3'
$LogFile version 2.0 is not supported.  (This driver supports version 1.1 only.)
$LogFile version 2.0 is not supported.  (This driver supports version 1.1 only.)
Did not find any restart pages in $LogFile and it was not empty.
The file system wasn't safely closed on Windows. Fixing.



The fix seems to be in progress, will update as soon as there is a result.

update: this was the case, i can acces the partition, it's just super-slow. will update again if everything worked. thanks for the advice so far.

---

### Post by ajgreeny on 2015-08-25
I suspect the Win8 drive was not mountable because one or more of the the ntfs partitions was still flagged as in use, either because the disk crashed, stopping windows in its tracks, or because windows had, as it does by default, not shutdown but hibernated the disk.

The disk really needs attaching to another windows machine to overcome this problem, not trying to do it with Ubuntu, which I hope has not harmed the filesystem of the disk.

---

### Post by Mark Phelps on 2015-08-25
> i want to rescue a friends data from a broken Windows 8 by using a Ubuntu live-CD. Problem is, that I can't mount the HDD 

Sorry, you're most likely NOT going to be able to do that.  Why?

Because Win8 introduced a new form of hibernation that was enabled by default.  This is known as FastStartup -- which is NOT the same as Fast Boot.  FastStartup causes all the partitions that were mounted when a Win8/Win10 instance shuts down to REMAIN mounted!  This prevents any Linux distro from opening or reading those same partitions because they can NOT be mounted -- again.

They only way I know to get around this is to attach the drive to another PC running Win8/Win10 and, using Control Panel -- Power Options --> change what the buttons do --> see options normally unavailable ... uncheck the box at the bottom of the window that says Fast Startup.  Then, reboot.  Then, shutdown (not Restart, ShutDown)  After that, when you disconnect the drive you should now be able to mount the partitions.

---

### Post by Jefferson1 on 2015-08-25
> **Mark Phelps said:**
> Sorry, you're most likely NOT going to be able to do that.  Why?

Because Win8 introduced a new form of hibernation that was enabled by default.  This is known as FastStartup -- which is NOT the same as Fast Boot.  FastStartup causes all the partitions that were mounted when a Win8/Win10 instance shuts down to REMAIN mounted!  This prevents any Linux distro from opening or reading those same partitions because they can NOT be mounted -- again.

They only way I know to get around this is to attach the drive to another PC running Win8/Win10 and, using Control Panel -- Power Options --> change what the buttons do --> see options normally unavailable ... uncheck the box at the bottom of the window that says Fast Startup.  Then, reboot.  Then, shutdown (not Restart, ShutDown)  After that, when you disconnect the drive you should now be able to mount the partitions.

I didn't know that. 
After my last step however (see my last post), i do have access to the HDD after ubuntu 'fixed' it. Trying to rescue the files right now. Many of them are broken and can't be copied. In these cases, Ubuntu says there is a input/output error. I don't know where this comes from, is it maybe because i didn't do it as you told? Or is the HDD broken anyway? The later seems plausible to me since Windows 8 broke out of nowhere (bluescreen with the message, that winload.efi is broken).
Shall I stop the process of rescueing files?

---

### Post by yancek on 2015-08-25
>  Windows 8 broke out of nowhere (bluescreen with the message, that winload.efi is broken).
Shall I stop the process of rescueing files? 		

I would think you could repair the efi problems with your windows installation medium.  Have you tried that?  I'm not a windows user so can't give any details on how you might do that.

---

### Post by Jefferson1 on 2015-08-25
I don't have a windows installation medium here. I will try as soon as i saved the data and got empty dvd's.

---

### Post by pmrlaw on 2015-08-26
I had colourably similar problems trying to install Vivid Vervet on a Macbook Pro some months ago (problems recognising a hard drive). A particularly lazy (for which read 'attractive') solution is to buy a SATA to USB hard drive caddy. Externally attach the hard drive whose data you want to copy or save by connecting the USB from the caddy to another windows machine. The advice from others here present, advising you NOT to try installing a linux distro until you have saved your windows data is absolutely correct.

If you enjoy new builds...and often swap hard drives around, a SATA to USB caddy is super handy for all sorts of reasons. You can use it to preserve or copy data. You can use it to externally attach a giant 4TB hard drive to one of your main computers by way of a 'super back up' of all your music and DVD movies (if you have digitised your DVD movies using the excellent handbrake program for example). Hence, if one of your hard drives has a melt down at some future point, the labour involved in copying key data back onto a new drive is minimal.

Getting back on point, an incredibly useful program you may want to have a look at is 'Parted Magic'. This is seriously useful software especially when you have a hard drive issue or want to run a memtest. I work as a tech and use it a lot. You can run it from the disc (ISO image) in 32 or 64 bit modes...you can even run it from RAM if you like....it allows fairly comprehensive testing of suspect hard drives without messing up the data on them.  You will have to enable the hard drive SMART capability from your BIOS screen to use the hard drive diagnostic features in Parted Magic.

My issue with the Macbook Pro was caused by the internal SATA cable dying due to mechanical stress over the previous 6 years (the cable connecting the hard-drive to the motherboard).

 Using a SATA to USB caddy helped me diagnose the cable problem, which was solved simply by getting a replacement cable on Ebay. That Macbook Pro is running Vivid Vervet so perfectly I simply cannot believe it. Tailor made. I am absolutely delighted not least as I now have a 1TB 2.5" drive in it...think vast numbers of movies to choose from on long train journeys.

In passing, it is always best to use the very latest version of Ubuntu or Xubuntu..however, I discovered that Vivid so happens to work amazingly well on 2009 Macbook Pros...hence the older version. Always best to use the very latest version of Ubuntu or Xubuntu on your main machine....in fact I am still in shock at just how good Ubuntu and Xubuntu now are. Cannot understand why anyone would want to use Windows or a Mac OS because there is enormously well informed support on the forums for things such as printer drivers and because the only other bugbear (occasionally non-trivial issues if you want to play Windows games) is now largely resolved via Playonlinux which continues to improve with every update.

---

### Post by Mark Phelps on 2015-08-27
> **Jefferson1 said:**
> Shall I stop the process of rescueing files?

NO ... If the hard disk is dying, you have limited time to rescue the files.  It can fail at any time.

---

