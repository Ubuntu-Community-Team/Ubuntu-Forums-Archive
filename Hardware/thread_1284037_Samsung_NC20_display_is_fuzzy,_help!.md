---
title: "Samsung NC20 display is fuzzy, help!"
date: 2009-10-06
forum: Hardware
---

### Post by Brainthor on 2009-10-06
Hey there, 

I've got a Samsung NC20 netbook, which shipped with Windows XP as standard. I created a Ubuntu USB start-up key, and proceeded to install Ubuntu on this netbook.

After booting from the USB drive, the loading bar displayed fine, but after that, the screen went extremely fuzzy. The screen was fuzzy for the entire installation process, aside from when the loading bar is displayed at start-up. After the installation process was complete, I had hoped that this problem would have fixed itself, but it hasn't. When I turn the netbook on, the bios displays fine, the Ubuntu loading bar still displays fine, but as soon as the loading bar has completed the screen turns into a scrolling blur of colours and vague shapes. 

I connected an external monitor to the netbook for the entire installation process, and the external monitor displays Ubuntu perfectly. Ubuntu seems to have a problem with the standard monitor on my netbook. I've tried changing the screen resolution and the refresh rate, to no avail. From researching this problem online, it seems I'm not the only person to suffer with it. However, I couldn't find another example of a person pursuing a fix for it. 

So, can anybody offer me some possible fixes or help? I'm very new to Linux (I used Ubuntu on an old PC a few years ago for about 2 weeks, which is just about all of the experience I have with it). From researching online, people seem to suggest fiddling with the xorg.conf file to adjust settings for the display, but I don't want to go messing with anything that will make my netbook even more useless than it already is.

Thanks for reading, and for any suggestions. This is really driving me mad!

---

### Post by Uli_of on 2009-10-06
Use search function with "NC20" on the board.
There is a log thread and also a installation wiki 
to be found.
Try to install the latest openchrome driver from svn.
Regards
Uli

---

### Post by Brainthor on 2009-10-06
Hey there. Thanks for the reply. I've tried following the tutorial on the Wiki, and I've tried other methods too. The message I get when trying to install the VIA drivers says, "Install the via driver! .../usr/bin/install: cannot create regular file '*long file path*': No such file or directory...... Done!", then it tells me that I need to reboot. I'm assuming it hasn't done anything based upon that error message, and when I reboot nothing has changed. 

I'm so frustrated right now. I have no idea how to operate Linux and install things, and every time I think I'm on to a fix I get some error message that completely stops all progress.

Has anybody else had this issue with the monitor? Anyone throw any ideas out there that might fix this?

Somebody posted their xorg.conf file information here for the same laptop. I assume we both have the same hardware. I was going to edit my xorg.conf with the details from the guy's file that worked, however I can't edit the damn file either.

---

