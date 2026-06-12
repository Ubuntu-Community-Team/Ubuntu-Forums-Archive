---
title: "Ubuntu freezes during first startup following Wubi install"
date: 2008-07-29
forum: General Help
---

### Post by beerslayer on 2008-07-29
Hi, all - Linux n00b here so please be gentle...

I have Wubi (Ubuntu 8.04) partially installed on an old AMD K6-based laptop (475MHz - no speed demon but should be enough to at least work) which is already running Windows 2000.  The Wubi installer complained about insufficient RAM (I have 192MB and it prefers 256) but it was able to continue and seemed to work OK.  Installer completed without further error and, when prompted, I restarted the system.

During this first restart, the Ubuntu splash screen came up OK, then a bunch of text messages flowed by, and then the brown background image with the multicolored bird filled the screen.  For a few seconds, the mouse worked normally, then froze.

Nothing else ever appears on the screen.  The mouse is not completely dead - if I move it, the pointer may move eventually but it will probably be several minutes before it moves.  The hard disk activity light flashes occasionally, indicating that there is some access taking place, but there is no feedback on-screen so I have no idea what it might be doing.

I've left this machine in that state for over 12 hours and nothing ever changes on the display.  I've eventually had to hard reset the machine just to get control back.  Attempting to boot Ubuntu again results in the exact same thing.  I have yet to gain control of the Ubuntu interface.

If Ubuntu is still doing something constructive at that point, it's being awfully slow about it.  I cannot afford to wait 24 hours for my machine to boot each time.

Is there a chance I've done something stupidly wrong here?  Not being familiar with Linux, it's entirely possible.

---

### Post by minhmeoke on 2008-07-29
If Ubuntu takes more than a minute to boot up, then there is a probably a hardware conflict somewhere; don't worry, you haven't broken anything. Does the keyboard respond (ie, does num lock light up when you press it)? If yes, then try going to a virtual terminal by pressing ctrl alt f1 simultaneously, this should bring you to full-screen terminal. If you cannot get to the virtual terminal, then your video drivers or xorg.conf file might be the issue.

If you can get to the terminal, try logging in, then enter the "dmesg | less" command at the prompt, you can scroll through messages with this. There should be some errors near the end, write these down and when you are done press q to quit back to the terminal. If possible, look up the error message here in the forums, chances are that someone has already experienced something similar and has found a solution.

You can also try restarting the X-server, which is the system for displaying graphics, with "sudo killall gdm", and then restart it with "sudo gdm".

---

### Post by ago on 2008-07-29
Your memory is really too low. You can ignore the warning, but of course there is no guarantee the installation will succeed. The minimum for a live CD installation is 256mb. You might try with Xubuntu that should work with less.

---

