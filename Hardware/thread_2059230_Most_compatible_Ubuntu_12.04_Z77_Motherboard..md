---
title: "Most compatible Ubuntu 12.04 Z77 Motherboard."
date: 2012-09-17
forum: Hardware
---

### Post by stchman on 2012-09-17
I am contemplating building a new system.  I have narrowed it down to two Intel Z77 motherboards.

ASUS P8Z77-V Pro
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131819](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131819)

Gigabyte GA-Z77X-UD5H
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545)

Does anyone have any experience with either of these motherboards using Ubuntu?

Thanks.

---

### Post by oldfred on 2012-09-17
This site as been using a high end ECS board.

[http://www.phoronix.com/scan.php?page=category&item=Motherboards](http://www.phoronix.com/scan.php?page=category&item=Motherboards)

I have seen a variety of models not sure which. But most have issues with the new UEFI with gpt partitioning or some revert to the older BIOS/MBR partitioning.

Some examples that worked, not everyone specified model of motherboard. Most worked around various issues and made UEFI work.

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

---

### Post by smgendler on 2012-10-14
I have a P8Z77-V Pro and I am having a few problems.  My sound is not working and I can't seem to bring up the sound function in 12.04 64bit.  I'm using an I7, and overclocking the memory.  I'll probably stop the OC and see if that helps.  When I go to Asus support, linux drivers are not on their web site.  I hope this helps.

---

### Post by Yellow Pasque on 2012-10-14
> **smgendler said:**
> I have a P8Z77-V Pro and my sound is not working
Please report a bug using the ubuntu-bug command.

---

### Post by stchman on 2012-10-14
The Asus P8Z77-V Pro worked OOB with 12.04 64 bit.  I used a Sound Blaster Audigy 2 Value sound card.

The Asus mobo was bad so I changed it in for a Gigabyte GA-Z77X-U3H and it works OOB as well with Ubuntu 12.04 64 bit.

---

### Post by smgendler on 2012-10-21
Ahh.  Maybe that's my problem.  I'm trying to use the built in Realtek.  I will report the bug.

---

### Post by smgendler on 2012-10-21
Serious question:  What do you do when ubuntu-bug has a bug?  I've never tried it before and it hung the machine!  I'll try again with sudo.  I love computers!

---

### Post by Yellow Pasque on 2012-10-21
> **smgendler said:**
> Serious question:  What do you do when ubuntu-bug has a bug?  I've never tried it before and it hung the machine!  I'll try again with sudo.  I love computers!
Get on Launchpad and file the bug manually: [https://help.ubuntu.com/community/ReportingBugs#Filing_bugs_at_Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing_bugs_at_Launchpad.net)

The package you want to select is "alsa-driver"

---

### Post by General_Faliure on 2012-10-22
Forget about Gigabyte, the mainboard may or may not be compatible, but Gigabyte doesn't support you if you so much as hint you are using Linux.
I have read about this in the Phoronix forums.

---

### Post by smgendler on 2012-11-11
My 12.04 is working for now.  I went to realtek.com.tw and downloaded their HD audio codec and ran their install script.  It's working fine now.  To their credit, they actually have linux software available for downloading.  I lied above.  I really do hate computers.

---

