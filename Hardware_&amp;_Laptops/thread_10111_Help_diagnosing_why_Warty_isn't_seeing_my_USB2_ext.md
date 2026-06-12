---
title: "Help diagnosing why Warty isn't seeing my USB2 ext hard drive..."
date: 2005-01-04
forum: Hardware &amp; Laptops
---

### Post by Zhivago on 2005-01-04
The drive is an Acom Data 120GB USB2/Firewire, FWIW.

Here's the deal: WinXP sees the drive fine, so it's definitely not malfunctioning. It's formatted FAT32 and is connected to an Adaptec DuoConnect USB2/Firewire card that does work in linux, as verified by my plugging in other devices into the card, such as my iRiver.

When I plug the hard drive in and turn it on, the light on the front of the drive blinks with activity for about 6-8 seconds, then is solid green, indicating normal operation with no activity.

If I go to Computer->System Configuration-> Device Manager, I can see both the USB card and the drive, but no drive appears in /dev, or in Computer->Disks or elsewhere in gnome. I expected the drive to be automounted and an icon to be displayed on the desktop, like with my iRiver and USB flashdrive.

I've run various distros for years now but never bothered to use the external drive with anything but Windows because Windows has always been my primary OS, but now that my goal is to use Ubuntu as my primary OS, I need to be able to access this drive. I would try the drive on the firewire connection to see if it would pick up, but I don't have a cable handy, and I'd like to solve the issue rather than avoid it.  I've googled to see if anyone else has had the same issue and I've come up empty, so I'm hoping you experts here can point me in the right direction.

I'm pretty much a novice when it comes to the guts of the OS, but if you guys need any logs or further info from me, let me know what I need to give you (and how to get it) and I'll post it here.

Thanks a bunch in advance.

---

### Post by Zhivago on 2005-01-06
Okay, so I moved all the data off the drive and reformatted it to ext3, thinking that might solve the issue.  I plug in the drive when running Ubuntu and it doesn't automagically mount, no icon appears, etc., as is the case with my iRiver music player.  What gives?  Is there something I need to do/configure in order for this external hard disk to be detected and automounted?  Clearly the fact that the iRiver is detected and mounted fine indicates that hotplug is working...  any help would be appreciated.  

Thanks again.

---

### Post by cacofonix on 2005-01-06
There is another post in the forums [*here*](http://www.ubuntuforums.org/showthread.php?t=9695)  about firewire drives not really getting picked up by gnome. Are you able to mount the drive manually? I suggested a fix there that won't mount it automatically but it will help you mount it quicker. What version of ubuntu are you using maybe if you were to make a bug report on it?

HTH

cacofonix

---

### Post by Zhivago on 2005-01-06
Mysteriously enough, the drive, now ext3, is recognized and automounted normally.  I can't explain it, other than the change in filesystems on the disk I did nothing.  FWIW I'm running Warty with the i686 2.6.8 kernel, pretty stock stuff, no Hoary packages at all.  Thanks!

---

