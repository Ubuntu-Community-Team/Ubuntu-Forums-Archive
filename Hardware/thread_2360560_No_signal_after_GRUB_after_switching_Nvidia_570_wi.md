---
title: "No signal after GRUB after switching Nvidia 570 with 460."
date: 2017-05-05
forum: Hardware
---

### Post by soonmoon2 on 2017-05-05
Hello,

I have replaced my graphics card which was Nvidia GTX 570 with 460 (I am no longer in possesion of GTX 570). To my surprise after going through GRUB2 and choosing boot option - signal to the monitor suddenly dissapears. System installed on HDD is Arch Linux, but I've tried live Ubuntu USB and after purple initializing screen (with keyboard icon at the bottom) I same thing happens. When I add "nomodeset" it's just stuck on some BIOS text which doesn't display anything helpful. I tried to boot Windows 7 USB and unlike Ubuntu one GUI Installer was able to start, but I don't have spare HDD to format and try to install it on. I've tested GPU on my other PC with Windows and after installing drivers it did run well.

What could I try in order to boot Arch or Ubuntu in live version?

---

### Post by paulisdead on 2017-05-05
You could try either the server or minimal install images, which are text mode only.  You'd be left with having to manually install a desktop environment afterwards, though.  Then you could also install the nvidia binary drivers, and it might work.

This might sound silly, but did you remember to plug in the 6 or 8 pin PCI-E power connector?  This does sound like what happens when you don't plug in the power to the card.

---

### Post by soonmoon2 on 2017-05-06
> **paulisdead said:**
> You could try either the server or minimal install images, which are text mode only.  You'd be left with having to manually install a desktop environment afterwards, though.  Then you could also install the nvidia binary drivers, and it might work.

The issue with that would be having to wipe a drive I guess? I cannot afford to do that yet. Also I wonder why Ubuntu USB installation doesn't even work. I guess that Arch could have incompatible drivers (even that 460 and 570 use the same I think), but why would USB installation fail to run...

> **paulisdead said:**
> 
This might sound silly, but did you remember to plug in the 6 or 8 pin PCI-E power connector? 

I often forget to do it, but not this time unfortunately.

Thank you for your reply!

---

### Post by soonmoon2 on 2017-05-07
I borrowed Nvidia 560 Ti from my friend and everything is working now.

---

### Post by oldrocker99 on 2017-05-07
Just a hint: Mark this thread as [SOLVED].

---

