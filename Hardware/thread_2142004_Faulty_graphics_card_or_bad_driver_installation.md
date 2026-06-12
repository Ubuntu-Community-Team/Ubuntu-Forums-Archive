---
title: "Faulty graphics card or bad driver installation?"
date: 2013-05-04
forum: Hardware
---

### Post by Drumber on 2013-05-04
So I have been having major problems with my graphics (Nvidia 660ti) after upgrading to 13.04. It was going to a blinking cursor when booted, so I uninstalled the proprietary nvidia driver.

I can now get to the desktop, although the resolution is stuck at 800x600. If I try to go to a text console (Ctrl + alt + F1) I am met with a black screen, although I can can back again no problem (Ctrl + alt + F7). If I try and enter the bios, again a black screen. I tried booting into a liveUSB, but I am still stuck at 800x600 with the same problems.

I have also tried reinstalling the nvidia drivers though their website, via apt-get and via the additional drivers menu. I made sure the correct linux headers were installed (as I had problems with this in the past) but in all cases I get a bunch of text and then a blinking cursor. Failsafe graphics mode does the same, and replacing "quiet splash" with "text" in grub drops me to a text login. Trying to start lightdm from there gives me a black screen.

I'm out of ideas and have tried everything I can from googling. Any help would be appreciated.

---

