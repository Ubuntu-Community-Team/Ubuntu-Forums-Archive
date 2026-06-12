---
title: "Ati drivers/switchable grahics?"
date: 2012-09-11
forum: Hardware
---

### Post by XrRydr on 2012-09-11
I've been trying to find a way to get switchable graphics to work on my computer.  I've got an ASUS b43s.  It has integrated intel graphics as well as an ati 6470m card.  I've read that the proprietary drivers work better than the open source ones, especially for switchable graphics.  I tried to follow this guide, but it didn't work for me:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I started at "Manually installing Catalyst 12.6, special case for Intel/ATI hybrid graphics"
To be fair, it said that installing 12.8 probably wouldn't work, but I'm not sure what else to do.  I followed the instructions and after the reboot at step 9 the computer said the graphics weren't properly configured and it had to work in low-graphics mode, which didn't work.  Fortunately, it had an option to revert to a generic backup which worked fine.  This is a wonderful improvement over the other distros I tried this with, for them I just installed a new distro over them and tried again.

For those who have intel/ati switchable graphics, what have you done that is most sucessful?

---

### Post by 2F4U on 2012-09-11
There is quite a big thread dedicated to this here on the forum:

[http://ubuntuforums.org/showthread.php?p=11712748](http://ubuntuforums.org/showthread.php?p=11712748)

As I read it, there is no solution available that works in general, but this thread has some interesting hints in it.

---

### Post by XrRydr on 2012-09-11
I saw that thread and it is useful, I was just hoping for some more up to date information.  Unfortunately I think the next thing for me to try is to go and reinstall windows to see if I need to update the bios.

---

### Post by Mark Phelps on 2012-09-12
If I had a dollar for every post I saw where someone presumed that updating the BIOS would solve one or another hardware-related problem, I could have retired years ago!

Updating the BIOS, unless you KNOW it fixes a specific problem, is NOT something you should be doing.

I use to think that was harmless, myself, until I made the mistake of updating the BIOS on a new Gigabyte motherboard -- and lost the ability to run my 1600 speed memory any faster than 1033!  I reflashed the BIOS back to the old version and the memory speed cap was removed.

This is a DRIVER problem, not a BIOS problem, in that Windows provides special drivers for properly handling switchable graphics but Linux does not.

---

