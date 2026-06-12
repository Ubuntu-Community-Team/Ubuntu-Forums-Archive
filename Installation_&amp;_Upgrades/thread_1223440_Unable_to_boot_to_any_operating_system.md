---
title: "Unable to boot to any operating system"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by Franco-zola on 2009-07-26
I am trying to run a dual-boot Vista and Ubuntu 9.04 machine on my Samsung R522 laptop.
 
Having shrunk an existing partition within Windows Vista by 40GB, I ran the Ubuntu installation program from CD and installed it to the largest area of free disk space.
 
Installation was initially successful, but when trying to boot up my computer again, but when faced with a choice of operating system to load up, I tried to open Vista and Samsung Recovery Solution program opened, instead of the operating system.
 
I exited Samsung Recovery Solution, and the computer restarted. Now I can't boot to either Vista or Ubuntu, and I get the message "GRUB Loading Stage 1.5" flash up on screen. The computer attempts to load up, but then automatically restarts - this happens continuously until I turn off the power.
 
I don't have a Vista recovery disk to reinstall, so would be grateful for any pointers about how to fix the boot up settings.
 
This happened the first time I tried to install Ubuntu alongside Windows, and I ended up having to do a second installation of Ubuntu and fiddle for hours trying to restore the MBR boot up. Is there an easier way to fix this?

---

### Post by AndyCee on 2009-07-26
I would recommend booting into a liveCD to look at the partitions in the partition editor (In System->Administration).

You should be able to fix grub following [these instructions]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by wojox on 2009-07-26
How did you shrink Vista? With the Disk management Tool?

---

### Post by WSmart on 2009-07-26
I've fixed grub errors by running a disk check.  You might try that with a LiveCD, Administration>partition editor.

I always recommend running Linux on it's own machine and using a KVM switch on the desktop, so you have your familiar OS at hand, no possible complications.

THANKS ALL!:popcorn:

---

### Post by merlinus on 2009-07-26
You might try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

FWIW, most people who dual-boot with windows and linux on one hdd have remarkably few problems.

---

### Post by Teabicky on 2009-07-26
[QUOTE=merlinus;7680704]You might try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)
QUOTE]

I second that.

---

### Post by Franco-zola on 2009-07-26
Thanks I have now managed to fix Grub following the link you gave, Andy Cee.
 
I can now boot back into my original Ubuntu install and into Vista.
 
Cheers

---

### Post by AndyCee on 2009-07-28
No worries. I bookmarked that howto a long time ago, and have referred to it at least three times *since* then.

---

