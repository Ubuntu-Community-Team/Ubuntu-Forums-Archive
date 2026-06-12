---
title: "Western Digital external drive is readable on Ubuntu"
date: 2017-05-23
forum: Hardware
---

### Post by xpeaceservant on 2017-05-23
Today I successfully loaded Ubuntu 16.04.2 LTS on an Intel Dual Core 2 Quad PC. It's partitioned with Win XP. Under XP the external one terabyte WD drive wouldn't function under XP.  It would show up as being plugged in.  That is it. It appears that the Windows driver was corrupted or missing, or whatever.

Here's the question; does Ubuntu use 'drivers' and I'm presuming whatever it uses was built into the Ubuntu build?

Thanks.

---

### Post by TheFu on 2017-05-23
USB storage drivers are built-into the kernel, usually.  That means that pretty much any USB storage should work.  I can't say **all** because someone might make something funny and not bother testing it with Linux.
Plus, some USB controllers could have issues with Linux.

I vaguely remember certain WD USB drives having issues a few years ago.  I've had a WD USB drive for about 4 yrs and never had any issues with it and Linux.  My drive has never been connected to Windows.

If you are really new, please know that NTFS cannot be used for Linux operating system. You'll need to format with EXT4 (or some other Linux file system). That would wipe all data on the disk - or on the partition.

---

### Post by xpeaceservant on 2017-05-23
So can the NTFS files be read at all and run?  There really is nothing important (yet) on this WD drive, so I'm happy to wipe it and format it for EXT4.

---

### Post by TheFu on 2017-05-23
> **xpeaceservant said:**
> So can the NTFS files be read at all and run?  There really is nothing important (yet) on this WD drive, so I'm happy to wipe it and format it for EXT4.

Think of NTFS as a "data only" storage device.  Not for programs, writing code, DVCS use or Linux OS stuff.  All of those need Unix-style permissions.

Best to format it as EXT4 and be done - or at least one 25G partition and whatever size you need for swap will need to be formatted as "swap."   Also, your HOME needs to be ext4 too.
* 25G for the OS - ext4
* 4-8G for swap - swap
* Whatever you need for HOME - ext4
* Then you can do whatever you want with the rest - if you want Windows to read it, NTFS. For data only.

If you go with encryption (IMHO, portable devices need to be encryted), then add a /boot with 1G of storage as ext2. That will setup LVM for the rest of the disk.  You can modify the LVs  (logical volume) sizes however you like. That's the power of LVM. Most new-to-linux people avoid LVM.  It is a powerful, flexible tool, but does add complexity.

---

### Post by xpeaceservant on 2017-05-24
Ok, good. I get that then.  "HOME" got my attention. I am unfamiliar with that other than as an abode.

---

### Post by TheFu on 2017-05-24
> **xpeaceservant said:**
> Ok, good. I get that then.  "HOME" got my attention. I am unfamiliar with that other than as an abode.

On Unix systems, each userid has a HOME.  The typical location on desktop Linux would be /home/thefu for me.  HOME is where all my files are placed by default. That's settings, configurations, data.  Ownership and permissions are critical for many of those files, so a Linux file system must be used.

It is common for people to use different partitions for HOME or /home/ so when they need/want to perform an OS update or even swap, then they can retain all their settings with minimal risk.  No need to spend 4 weeks tweaking settings for every app, like in that other OS.  And if you make a list of the installed packages, then you don't have to manually re-install them on a fresh OS install either.  Takes about 45 min for me to get a fresh OS install back to "my" install.  It completely changes the game from the way that other OSes work.

Of course, /home/ is just the default.  HOME can be placed on any storage, local or networked, provided the userid has access and control permissions.  In a business, it is common to place the HOME for each userid on different network storage.  I've seen 3K users handled this way with access to the same HOME from any of 1K different computers. Often, these systems run different operating systems - AIX, HP-UX, Linux, OSF, Digital Unix, Irix, Solaris - basically almost any Unix-like OS can share the same physical HOME.  Since scripting across all Unix-like OSes is almost exactly the same, running the same scripts can happen across most of the systems too.

But none of that matters.  Just know that the OS is very flexible, when you know what is possible.

If you want more details:
[https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/](https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/)
[https://en.wikipedia.org/wiki/Home_directory](https://en.wikipedia.org/wiki/Home_directory) <--- they spend way to much time on Windows' version.

---

