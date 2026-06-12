---
title: "Toshiba Satellite"
date: 2013-03-10
forum: Hardware
---

### Post by BigD77 on 2013-03-10
Got a hardware question that's driving me nuts (And that's a short drive!)  :)

I picked up a used Toshiba Satellite P305D-S8829 running Windows 7.  As long as I just Windows, it runs fine.

However, when I run Ubuntu 12.10 off of CD (Or any OS off of CD or USB stick), that runs great.  But when I shut the machine down and try to run Windows again, it fails to load.  I try to run it in Safe Mode, run start up diagnostics to fix the problem (and it comes up as Boot corrupted), and ultimately have to revert back to System Restore before Windows will load again.

This is frustrating, since I realize that the hard drive doesn't get used when I run from CD or USB stick, just the CD/DVD/USB stick and memory.  What could the problem be?

---

### Post by oldfred on 2013-03-10
Are you hibernating?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by BigD77 on 2013-03-10
> **oldfred said:**
> Are you hibernating?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

No.  I totally shut off the laptop.  Then I start it, hit F12, and boot from CD.  And I'm running Windows 7.

---

### Post by oldfred on 2013-03-11
Is this a new enough system to be UEFI/BIOS and you are booting in UEFI mode from flash drive?
Or is Windows running some sort of DRM software or agressive virus checker.

BIOS does write info to drive and if booted in UEFI mode data is different. Full power down & reboot should reset, but with laptops full power down is difficult.

---

### Post by BigD77 on 2013-03-11
> **oldfred said:**
> Is this a new enough system to be UEFI/BIOS and you are booting in UEFI mode from flash drive?
Or is Windows running some sort of DRM software or agressive virus checker.

BIOS does write info to drive and if booted in UEFI mode data is different. Full power down & reboot should reset, but with laptops full power down is difficult.

I don't know if it boots in UEFI mode.  This is an older laptop (2008-2009 vintage) that I picked up used.  How would I be able to check?  Windows 7 doesn't have the "Hybrid Shutdown" mode to be shut off, if it even exsists in Windows 7.  That option wasn't available.

I was using the CD for Ubuntu.  But previously I tried to use a USB drive to load Ubuntu to test.

I wanted to do a dual boot with Ubuntu 12.10.

---

### Post by oldfred on 2013-03-12
Very doubtful that system has UEFI. That only started with Intel i-series chips and most Windows were still installed in BIOS mode with even those systems.
I do not have Windows 7, but think you have to turn hibernation on, or not fully shutdown when rebooting.

---

### Post by BigD77 on 2013-03-12
> **oldfred said:**
> Very doubtful that system has UEFI. That only started with Intel i-series chips and most Windows were still installed in BIOS mode with even those systems.
I do not have Windows 7, but think you have to turn hibernation on, or not fully shutdown when rebooting.

Ok, thanks.  This laptop has an AMD processor.  There is no hibernation that I could find on Windows 7.  

When Windows 7 talked about dual booting, they mentioned placing the older system (Windows XP, 98, ME etc) on before Windows 7.  Don't know if you have to do the same thing with Ubuntu.  Doesn't make much sense.

---

### Post by oldfred on 2013-03-12
Windows does not see nor know about Linux. It does not have drivers to see the ext4 partitions.

Older versions of Windows do not know about new versions, but then the new version will update and allow dual  booting of Windows. So order of installs of Windows can be important.

Is Windows on the first drive?

---

### Post by BigD77 on 2013-03-12
Windows is on the first drive.

Turns out that Windows 7 DOES have a hibernate feature.  Here is a video on how to disable it:

[http://www.youtube.com/watch?v=beAx4mGfMv0](http://www.youtube.com/watch?v=beAx4mGfMv0)

In playing around with settings before seeing this video (With help from the links you gave), I was able to disable the hibernate and run Ubuntu from CD without any problems to Windows.  Now to load Ubuntu 12.10 and dual boot.   THANKS!!!

---

