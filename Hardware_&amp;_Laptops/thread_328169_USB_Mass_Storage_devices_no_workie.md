---
title: "USB Mass Storage devices no workie"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by CA_Warren on 2006-12-30
*Initial Disclaimer: I'm using Kubuntu.*

I recently upgraded to Edgy Eft, and am now having issues with USB mass storage devices - namely, a camera and a CompactFlash card reader.

When I connect either device, the Auto-Dialog comes up, asking what I'd like to do with them. If I select "Import Photos to digiKam", digiKam opens then gives me a dialog saying 'Failed to List Files in /camera'. If I choose to open the device in a new browser window in Konqueror, it lists the device as sda1 and opens a folder that it insists is empty (whereas there should be files there).

I've tried the camera in both 'PC Mass Storage' mode as well as in 'PTP - Camera' mode - Kubuntu recognized both, but did the same thing each time.

(Yes, the camera is compatible with digiKam, but even if it weren't there's no reason the CompactFlash reader would also be on the fritz...)

Any ideas at all what's up? Are there packages I should try reinstalling here?

I'd be glad to post error logs/dmesg output, if you'd let me know where to find those. Any help would be very much appreciated, it's hard to take pictures knowing they have to stay on the camera...


**NOTE: I apologize if this problem has been listed before, I had troubles getting the forum 'search' feature to produce any meaningful results at all.**

---

### Post by CA_Warren on 2006-12-30
Anyone? Any ideas at all?

---

### Post by hinge on 2007-02-03
I have the same problem...
I have further found that when I start digikam as root everything works like a charm...
before I upgraded to edgy all was fine....
Is it a rights thing on some usb devvice in /dev/.....

Martin

---

### Post by CA_Warren on 2007-02-03
Hey,

My solution was to boot using one of the other kernels offered at system boot (hey, if Kubuntu's going to keep around every version of the kernel you've ever had, you may as well use them).

Using the second-to-most-recent version seemed to make everything work for a while. One day it didn't, and upon booting into the normal, most-recent-kernel, everything worked fine again.

Sorry this is anecdotal and not a real solution, but that's the way it all played out for me. If you're still having trouble, it may not hurt to boot using a different kernel. Good luck to you! 

(and if you find the real root of the problem and/or a reliable solution, please post it back here so other folk who encounter this don't have to wander confusledly)

---

### Post by Chris11 on 2007-02-05
I can't write to the CF card, connected to a USB card reader and can't change permissions as well. The card is FAT16 formated. I'v got a thread bout this problem without answers 'till today.

[http://www.ubuntuforums.org/showthread.php?t=351786](http://www.ubuntuforums.org/showthread.php?t=351786)

Chris

---

