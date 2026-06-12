---
title: "System freezes after installing ATI restricted drivers"
date: 2008-06-03
forum: Hardware
---

### Post by crazyfoq on 2008-06-03
Hello,

I have a contently reoccurring problem when trying to setup Ubuntu 8.04. 
What I do: I install Ubuntu on my 2nd hard drive (does not share anything with the windows drive, and the boot loader is also installed on this (the Ubuntu) hard drive). Restart, and install updates, restart again. Now install the restricted driver (through the restricted drivers manager) for my video card (video card and system information below), after that I need to restart again. 

The problem: I get the Ubuntu loading screen, the progress bar (the orange loading bar at start up) completes, and as soon as the system leaves this screen it hangs. I all see a black screen and keyboard is also unresponsive.

System info:
Processor: Intel Core 2 Duo E8400
Mainboard: ASUSTeK - P5K
Videocard: MSI RX3870 (T2D512E) 512MB - DDR4

Please try to be detailed as possible if you have an idea or solution to my problem, I am new to the Ubuntu experience.

Thanks in advance for the help!

---

### Post by crazyfoq on 2008-06-03
I've been trying to solve this problem and have gotten past the black screen where the PC turns unresponsive. 
I forgot to mention that I am running Ubuntu 8.04 64 with 4GB of memory. 
The problem I am having now is that when I login to my account I get a white screen (of death?), my keyboard is still responsive though. 
I am able to boot into "safe mode" of gnome and from what I've read I should try to get Hardy working with all of my memory. To do that I followed [http://ubuntuforums.org/showthread.php?p=4766662](http://ubuntuforums.org/showthread.php?p=4766662) and after I've completed that and do "cat /proc/mtrr" I get write-back at all the regs, so I assume that has worked. However when I log onto gnome (in normal mode) I still get the white screen.

Any ideas?

---

### Post by markbuntu on 2008-06-04
If you can get into gnome in safe mode then you have a problem with your video driver setup for x and gnome sessions. Check your Xorg.0.log and look for any line with (EE). 


There is another thing you can try. Get in in gnome safe mode and set desktop visual effects to none. You can do this by clicking anywhere on the desktop and the menu will pop up. Then, when you restart, change session to run xfce script or run gnome script or something like that instead of the top option which is the default which is "run previous session" which is obviously not working for you. If that works, you should be able to log in normally, or at least without getting the white screen of death.

btw, ATI says the 8.47.3 driver, which is the one in the repos, does not support the 3870 card. The new 8.5 driver might, I do not know. You might try the ATI site for more info.

---

