---
title: "Best cross platform file system?"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by Aleksandersen on 2006-10-11
Hi,

**What is the best cross platform file system for an external, USB hard drive?**

I will primarily use the disk with Ubuntu Linux and Mac OS, but on rare occasions with Windows too.

Now; I have been unable to figure out how to write to a HFS+ *(Mac OS Formatted Journaled)* from within Ubuntu and to read and write to a HFS+ disk from Windows requires [expensive, commercial software](http://mediafour.com/products/macdrive6/). So HFS+ really is not the best choice.The other and most reasonable choice would be to go for a FAT32 formatted drive. But this brings with it issues too. It will turn the drive very slow and it will have strict limitations regarding file names and extensions.

So what is the best file system to use on an external drive that needs to be accessible and writable from all systems? And which tool to format it with to ensure maximum compatibility? I read somewhere that the tool I used to format the drive with would have much to say regarding the disk's preformance and compatibility.

**And what is the best file system to use on a local hard drive?**

The local drive will be access over my local network by Mac OS and probably from the computer when it is running Windows.

---

### Post by mssever on 2006-10-11
Windows can handle an ext2/3 filesystem with an opensource driver. I don't remember what it's called, but you can probably google it up. I'm guessing that MacOS can use ext2/3, as well. So ext3 would be my first choice (depending on the Mac, of course--I don't own a Mac).


EDIT: see this thread: [http://ubuntuforums.org/showthread.php?t=275232](http://ubuntuforums.org/showthread.php?t=275232)

---

### Post by Magnes on 2006-10-11
[http://fs-driver.org](http://fs-driver.org) - only ext2 writing is safe, it's a little slow though. I think fat32 is the best choice for now.

---

### Post by efrenefren on 2008-05-18
Ubuntu fully supports writing to NTFS filesystems since Gutsy Gibbon
[http://www.ubuntu.com/testing/gutsybeta#head-cfd16f3029f2fc55199eefdc0ede604f4d4cf5da](http://www.ubuntu.com/testing/gutsybeta#head-cfd16f3029f2fc55199eefdc0ede604f4d4cf5da)

---

