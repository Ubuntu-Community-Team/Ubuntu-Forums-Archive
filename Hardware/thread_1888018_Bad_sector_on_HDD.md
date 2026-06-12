---
title: "Bad sector on HDD?"
date: 2011-11-28
forum: Hardware
---

### Post by kr651129 on 2011-11-28
I have an old PC that I'm using for a 11.10 32bit home server, dns, samba, printers, etc.  I have several old hard drives.  A grab back of SATA and whatnot.  I've installed a SATA controller and set up the pins on all of the HDD's correctly and created a software raid.  I think I'm running into some bad sectors on one of my HDD's because it gets to the software selection (aptitude) and when I select what I want installed it errors out on me.  Sometimes it error's out when creating the raid and other times it's just slow.  That being said I know to check the installation media so while I'm at work I'm going to burn another copy of 11.10.  But let's say for a second that the HDD does have a bad sector, is there anyway to either repair it at install or section it off so I can use the rest of the disk with a 3rd party utility?  It's on an OLD OLD OLD dell machine, not sure what the specs are.  Something else that is odd is, I can create a raid with 3 non-sata drives, I can install on just the sata, but it seems that the error is when I'm trying to use all of them in the raid.  Thoughts?

---

### Post by sudodus on 2011-11-28
I think there are problems when you mix SATA and non-SATA drives in RAID, maybe because the order they are given partition IDs (sda1, ...) can vary. I have seen another thread in the Ubuntu Forums about that.

I guess you can pull out a drive that you think is bad and check it thoroughly (low level) with ddrescue not caring about partitions and formatting.

I don't know, but there should be tools to check for read/write error for RAID. What about S.M.A.R.T? Is the drive new enough to have that (or is it de-activated in RAID)?

---

### Post by kr651129 on 2011-11-28
I'll try and give as much information as I can as I'm not at my PC.  When I create the RAID it names all of the disk's fine. hda, hdb, hdc.  hdc being the SATA.

I'm not sure if the drive is new enough to have SMART on it or not, I would assume so if it's a 320GB SATA drive but I'm really not sure.  I'm the System Admin at my work so when old machines are on their way out the owner lets me part them out as long as they arn't needed around the office so I was able to save some HDD's last week.

That being said, I would think that you can mix SATA and non-SATA but I think the problem here is the controller card since the other drives go right to the mobo and this one is via controller on the PCI bus.

---

### Post by BC59 on 2011-11-28
Sorry to say but for me the best way to check a disk and fix errors is CHKDSK.

If you have the ability to use Windows on the computer run twice CHKDSK /f and reboot. Or you can extract the HDD and use it as an external HDD to check it on Windows.

---

### Post by sudodus on 2011-11-28
> **BC59 said:**
> Sorry to say but for me the best way to check a disk and fix errors is CHKDSK.

If you have the ability to use Windows on the computer run twice CHKDSK /f and reboot. Or you can extract the HDD and use it as an external HDD to check it on Windows.
Yes, if it is a windows file system for example NTFS or FAT32. I would even suggest
```
CHKDSK /r
``` to check not only the file system but all sectors.

Would it work with RAID?

---

### Post by BC59 on 2011-11-28
> **sudodus said:**
> 
Would it work with RAID?

I wouldn't do that. CHKDSK was designed for a single hard disk drive device.

---

### Post by kr651129 on 2011-11-28
Well the more I think about the situation the more I'm starting to think that it's the installation media for the following reasons.

1. It never fails in the same place
2. It most commonly fails at package select (aptitude)
3. I am able to get it to install on a single disk but I'm still having odd errors that I shouldn't be getting (bad libc6, etc)

So I just reburned the media at 4x and I'll try again after work.

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

This says nothing about diffrent hdd's or hdd's of diffrent sizes.

But I would still like to see information otherwise if any of you have come accross it.

Edit:
And I would still like to know how to fix a bad sector in linux

---

### Post by BC59 on 2011-11-28
> **kr651129 said:**
> 
And I would still like to know how to fix a bad sector in linux

Well there is always smartmontools to do it.

---

### Post by kr651129 on 2011-11-28
Will that work on a raid config?

---

### Post by BC59 on 2011-11-28
You can but don't ask me how. It's not so easy.

---

### Post by kr651129 on 2011-11-28
Ok so it was a combination of a few different things it was a bad DVD and I had some bad sectors so I replaced the drives and reburned the media.  I ran into a few weird errors but that was because I'm trying to run a 5 disk software raid with an old school computer.  I configured a RAID 0 with 4 ata drives and one sata, none of the drives match in size, manufacturer, or  bus, but it does work.  I reinstalled the system a few times to tweak it, but it is now working.  I'll try to repair bad sectors with the suggestions above and let you all know how it works out.

---

### Post by kr651129 on 2011-11-29
I have some more useful information for all of you.

fsck does work on RAID.  After I got my RAID loaded I started to fill it up with data, after a reboot the system found bad sectors and ran fsck correcting these.  I did have some orphaned files, so I deleted all data and reloaded it so I could make sure nothing was corrupt.

---

