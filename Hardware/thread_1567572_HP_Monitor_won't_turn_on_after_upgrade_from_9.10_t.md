---
title: "HP Monitor won't turn on after upgrade from 9.10 to 10.04/error code included"
date: 2010-09-04
forum: Hardware
---

### Post by TonyChaos on 2010-09-04
Hey all,

I recently updated my HP Media Center m7640n from Ubuntu 9.10 to 10.04 and the upgrade went smoothly. It updated and downloaded all the right stuff I guess, then told me I needed to restart the computer. I did so, and when I did the monitor would turn on, there would be a blinking _ at the top left of the screen, then the monitor would go into power saving mode, but the PC would still be on. I could hear the hard drive doing something as well.

I got my HTC Evo and took a video of the booting process and got a chance to pause it and get this code to flash on the screen for a split second:

[	14.8218850 nForce2_smbus 0000:00:0a.1: Error probing SMB1

I don't know what to do! I have a bunch of movies and tv shows on another Linux drive that I can't get to because I can't even get the machine to boot.

Help please!

---

### Post by TonyChaos on 2010-09-05
Also, I've tried several different versions of Linux. openSUSE 11.3 gets to the boot screen, I select to boot regularly and I see the status bar move an inch, then the monitor turns off.

Ubuntu 9.04 is the only one that seems to boot correctly. Any guesses why?

---

### Post by TonyChaos on 2010-09-15
So I figured out the issue. It was an onboard video error. Apparently they got rid of video drives in the installation procedure. Put in a new graphics card just to get it to freaking work.

Thanks for the 100+ views and no responses. Major fail, Ubuntu Forums. Major.

---

