---
title: "Sandisk Cruzar USB Drive not Found"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by HLS on 2005-12-20
One port on the front panel of the computer appears to mount my USB drive, but I cannot find any listing of it.  The other port makes only a feeble effort and then quits.  Is there no automatic display of the USB drive when it is mounted?

---

### Post by wanger123 on 2005-12-21
Hi there, this is totally bizarre behaviour. If I plug my Dell usb key in, it gets mounted automatically on the desktop and I can browse the files in a new tab in konq, but if I plug in my SANDISK CRUZER MICRO usb key, it gets mounted on the desktop and a new tab opens but it fails with some error about fstab, mtab etc......... But if I then hit refresh in konq, everything is OK and I can browse the files. It must be a SANDISK-specific quirk methinks???? :confused: 
[EDIT] Also when you select 'safely remove' dell usb unmounts and disappears from desktop, SANDISK unmounts but stays as an unmounted icon. Come to think of it, I bet Breezy is treating these two usb keys as different device types. 
Well I discovered that it is NOT a SANDISK problem. It seems that which ever is first plugged in works fine, but the second and subsequent devices all have the aforementioned problem which requires a refresh to get working. (No biggie I guess)

wanger

---

### Post by jliedeka on 2005-12-21
There is probably some hotplug voodoo you can do to make that work.  I always disallow any type of auto-mounting (except my hard drive partitions) because I don't trust the OS to get it right.  I have one mount point defined for USB devices and a manually mount one at a time when I want to use them.

There is probably a way to have specific devices associated with specific /dev etries (and therefore mount points) but I've never cared enough to research it.  I'd poke around the documentation for the hotplug subsystem.

---

### Post by HLS on 2005-12-30
I owe an update to this post.  I replaced my onboard Nvidia video chip output with an ATI Radeon 9000 card and the Sandisk now works perfectly on both USB 1.1 and 2.0 connections.  Although the onboard Nvidia video chip makes for a very affordable mainboard/video combo, the chip is rather exotic, and drivers are not readily available in any Linux distro.  The ATI 9000, on the other hand was chosen because of universal acceptability in virtually any distro.  Now if Ubuntu can just fix the floppy ID problem and extend resolution to 1280 X 1024 for my Sony monitor, I will be ready to take a full plunge.  :cool:

---

### Post by HLS on 2005-12-30
New report!  Sandisk works AOK with the Live CD but is still undetected on the full HD install.  Since floppy also is not detected, I am still on hold on full acceptence because of inability to store temporary data an a "quickie" drive.  I will be eager to get the bugs out because this OS support is headed in the right direction (no criminal investigation of the hard drive.)  ;)

---

### Post by raghav_p on 2006-01-02
Wait.. my USB Sandisk Cruzer Key worked fine; it doesn't anymore. i think it's a problem with either hotplug or gnome-volume-manager; 

# lsusb returns this:
> 
Bus 004 Device 003: ID 0781:1234 SanDisk Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


meaning that its recognizing the key.

---

