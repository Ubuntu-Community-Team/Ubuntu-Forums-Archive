---
title: "kernel panic - even just with Live CD"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by jmkpost on 2009-07-30
I have been running 9.04 (32 bit) on my desktop AMD Athlon 64 X2 for some weeks without problems. Yesterday I accepted upgrades which included 2.6.28-14 kernel.
 
I had kernel panics afterwards and on one attempt with GRUB menu I managed to reboot via recovery mode. After I thought I was back in business I had rebooted, and no measure has been successful to reboot - alway locking up.
 
Then I tested my RAM (it was OK).
 
Then I disconnected my SATA drives (2 of them) so I had no HD, and loaded the Live CD (which I had previously used before installing to the HD)
 
With no HD and just the Live CD, I get:
 
Kernel panic - not synching: Attempted to kill init!
 
Thinking there may be another lurking hardware problem, I went into the BIOS and disabled most of the mb items such as SATA controller, usb, ports I do not use, etc.
 
Same result on Live CD boot.
 
Any ideas?

---

### Post by dlmarti on 2009-07-30
This really seams like a hardware issue.
When you say memory test, did you run memtest86?  Like for a while?

---

### Post by jmkpost on 2009-07-31
I ran the test for an hour or so. While I agree that the symptoms are of a hardware problem, the 'coincidence' that all of this was on the heels of apparently flawed update files is troubling. I can't help but think the updates caused the hardware problem somehow.

---

### Post by irohaphoto on 2009-09-23
> **jmkpost said:**
> 
 
Kernel panic - not synching: Attempted to kill init!
 


I get this same error and I have searched every where and cannot find an answer.
I have added a screen shot of the error here in my ubuntu forum gallery:

[http://ubuntuforums.org/album.php?albumid=1378&pictureid=4770](http://ubuntuforums.org/album.php?albumid=1378&pictureid=4770)

[http://ubuntuforums.org/album.php?albumid=1378&pictureid=4775](http://ubuntuforums.org/album.php?albumid=1378&pictureid=4775)

Apparently every time I boot up I get a different screen with the "Kernel panic - not synching: Attempted to kill init!" at the bottom.

A memory test all night reveals all red areas but BIOS is accessible if only I knew if there was something I could do there. I can get the GRUB prompt but not sure what to do there either.

I heard that "adding "noapic" sometimes helps with the Kernel Panic error message."
problem is what do I do with "noapic"? type it in at the grub prompt? edit one of the ubuntu selections?

Ubuntu 8.04.3 LTS I tried installing the latest version 9 but cannot get beyond the "Kernel panic - not synching: Attempted to kill init!"

ASUS Z9100E
AMIBIOS ver. 203 
intel pentium M  730  1600MHz
Memory 752MB

I contacted Asus head office and they said take it in to have an Asus technician look at it. Unfortunately Asus technicians don't live next door to me and if one did the 3 year warranty is out of date.

Any help would be appreciated.

---

