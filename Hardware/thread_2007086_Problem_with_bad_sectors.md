---
title: "Problem with bad sectors"
date: 2012-06-20
forum: Hardware
---

### Post by jackluu on 2012-06-20
I am having some bad sectors in my 1.5 TB hard drive (screenshot). Can any one tell me how to solve this problem in ubuntu. I know that if it is an fat or ntfs partion, we isolate the sector and prevent the system from writing and reading those. Can we do the same thing in ubuntu. I can still use this hard drive, but when I copy anything from the hard drive to other places it says "input/output" error while copying.

---

### Post by ahallubuntu on 2012-06-20
You don't "isolate" bad sectors in the operating system anymore.  The drive's firmware does that automatically.  In fact, it already has for a few bad sectors.  You are showing 3 Reallocated Sectors; those are the bad sectors already isolated and replaced with spare sectors.  There are 9 more pending sectors that the drive firmware has as yet been unable to access and replace.

The drive may be failing and you would not want to use it.  One thing you COULD try is to erase everything on the drive and write zeros to it (not the same as just formatting it).  In Linux, you can open a terminal and type this:

sudo dd if=/dev/zero of=/dev/sdX bs=2048

(replace /dev/sdX with the device letter of the 1.5TB drive.)

This command will take a while, hours probably.

WARNING, THIS WILL ERASE EVERYTHING ON THE DRIVE, and make sure you have the correct device letter!!!  The dd command is dangerous if typed incorrectly - if you give the wrong device say your boot drive you will erase it very quickly and it cannot be undone.

It should go without saying that you have already tried to backup everything on this drive before attempting to clear it.

After writing zeros, you can check S.M.A.R.T. again and see if there are any pending sectors left.  If there are, your drive is probably bad and can't be used again.  But reallocated sectors may actually go up.  A few reallocated sectors isn't catastrophic for an older hard drive, as all modern drives have some spare sectors, but if the drive surface is failing and more and more sectors must be isolated/replaced, eventually the drive will run out of spare sectors.

---

### Post by gordintoronto on 2012-06-20
In any case, you should plan to replace your hard drive.

---

### Post by Sef on 2012-06-20
> It should go without saying that you have already tried to backup everything on this drive before attempting to clear it.


To clone your current system, use [Clonezilla]("http://clonezilla.org").

---

### Post by Doktor Who on 2012-06-21
> **jackluu said:**
> I am having some bad sectors in my 1.5 TB hard drive (screenshot). Can any one tell me how to solve this problem in ubuntu. I know that if it is an fat or ntfs partion, we isolate the sector and prevent the system from writing and reading those. Can we do the same thing in ubuntu. I can still use this hard drive, but when I copy anything from the hard drive to other places it says "input/output" error while copying.

In such cases I've tried many solutions (in the years 1999-2004),  and finally I found a software named [**Spinrite**]("http://en.wikipedia.org/wiki/Spinrite") , that is the most effective tool you can use; it runs from a boot-diskette and operates in DOS environment; it **can **restore damaged sectors, but it may take many hours, up to 2 or 3 days, however you can specify the areas that you want to scan;  it doesn't work well on external hard drives, therefore you must mount your hard disk in any of your internal slots. Best wishes :)

---

### Post by jackluu on 2012-06-22
Thank you all, guys. I understand that buying new hd seems to be the only good solutions, but I really want to back up those data. I will give all of your suggestions a try this weekend. I just want to copy my files to safe place. I will tell you the result later. Hope that I can do the back up.

---

### Post by sudodus on 2012-06-22
I have good experiences with ***ddrescue***. It is a command line tool, that can clone whatever is possible to read from a failing drive.

The info page is very well written with general information as well as some typical examples how to use the program. ```
info ddrescue
```

You should run the program booted from another drive (not the drive that you intend to clone). For example you can boot a live session with an Ubuntu CD or USB drive and install ddrescue into that, or you can download a linux rescue iso file with ddrescue included, make a CD or USB drive and run from it.

---

### Post by buntuforums on 2012-09-30
You can use **PBD(Partition Bad Disk)** to isolate the bad sectors while creating the partitions. Then the partitions are clean of bad sectors.

---

