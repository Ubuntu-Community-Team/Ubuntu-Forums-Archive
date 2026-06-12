---
title: "Ubuntu &amp; Linux Mint Multiple Graphic Card Drivers"
date: 2015-10-25
forum: Hardware
---

### Post by kennysiphone09 on 2015-10-25
I am new to the Linux world and thought I'd give it go. I ran into a  problem early on that I can't seem to find any real specific information  on although many people have had similar problems. I am currently  running Linux Mint but I had this same problem on Ubuntu 15. Which is  what lead me to Linux Mint hoping for an easy solution.

  The problem is this...I have 2 Graphic cards in my computer that  operate 3 monitors all connected via DVI. Only 2 of them are working.

  Graphic Card 1 - Nvidia GeForce GTX 460 
Graphic Card 2 - Nvidia GeForce 8400 GS Rev 3

  On a fresh install, all 3 screens are on and work fine. However, the  display is not sharp, text is hard to read, the cursor blinks all the  time as I move it and it's just terrible to look at. My solution was to  update the drivers. This is where my problem came in. Of course the  system defaulted to using the Nouveau drivers on the fresh install and  without changing that, all 3 screens will work. 

  If I update the driver for Card 1, when I reboot and go back to the  driver manager, it does not show Card 2 anymore. However, if I look at  the Nvidia X Server Config Tool, it shows me all 3 screens albeit 1  shows disabled. No matter what settings I apply in the Nvidia X Tool,  that 3rd(disabled) screen does not come back on.

  If I update the driver for Card 2, I still have 2 displays working, nothing changes.

  I have tried ignoring/blacklisting the Nouveau drivers by modifying  the /etc/default/grub file with nouveau.blacklist=1. That did nothing. I  also tried modifying the xconf file and that did nothing but generate  errors when I reboot. I have had to re-install Linux 3 times now because  it wouldn't reboot after modifying the xconf file. 

  So there is some context to my problem. 2 Graphic Cards, 3 monitors  and only 2 of them will work. How can I get all 3 of my monitors  working?

  Update: I forgot to mention, I'm currently using the  "nvidia-340-updates : Version 340.93-0ubuntu0.0.1 : NVIDIA binary driver  - version 340.93" driver for the GeForce 8400 card. The GeForce GTX 460  card is still running the "xserver-xorg-video-nouveau : Version  1:1.0.10-1ubuntu2 : X.Org X server -- Nouveau display driver" driver.

---

