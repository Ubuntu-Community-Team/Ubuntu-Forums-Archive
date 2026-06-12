---
title: "HELP! GRUB gone mad?!"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by diyfiesta on 2007-12-16
Hello folks,

Just wondered if someone could give me a few pointers on my newKubuntu 7.10 install please? I've been running it for a couple of weeks when I had the genius idea of putting in another harddisk, when I booted up with both the gusty and new harddisk, it actually booted the new disk first (which had fedrora on it).

From them on, I can't boot the orginal kubuntu disk anymore! It gets to the point where it would boot but just says

GRUB _


and doesn't respond to user input or in any other way do anything! 

Any ideas! When it started to boot the other disk with fedora on, it spent a few moments anylising the disks, I'm wondering if it wrote something to the gusty disk and somehow broke the GRUB?

Is there such a thing as a rescue CD? a way of just sorting out GRUB? I can't boot... nooooooo

er, thanks for any tips :)

---

### Post by elliotjreed on 2007-12-16
There are 2 easier ways of sorting it out, botth using the Live CD and are on this post:

[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

Hope this helps!

---

### Post by logos34 on 2007-12-16
> **diyfiesta said:**
> ...I had the genius idea of putting in another harddisk, when I booted up with both the gusty and new harddisk, it actually booted the new disk first (which had fedrora on it).

From them on, I can't boot the orginal kubuntu disk anymore! It gets to the point where it would boot but just says

GRUB _

Sounds like kubuntu disk got bumped to second position in the bios hard disk boot priority as soon as you installed the fedora disk. But it shouldn't have altered grub or anything on the kubuntu drive.  If you're getting 'GRUB' to appear at all then it would seem you changed the bios boot order so the kubuntu disk is first--is that what you did?  But it should boot at that point.  What type of drives are they--sata, pata/ide?

Reinstalling grub to mbr using the link elliotjreed provided may get the menu screen to show up but you may have to edit the 'root' line to get it to boot kubuntu

---

