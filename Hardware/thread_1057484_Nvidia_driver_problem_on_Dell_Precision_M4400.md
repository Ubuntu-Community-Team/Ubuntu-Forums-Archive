---
title: "Nvidia driver problem on Dell Precision M4400"
date: 2009-02-01
forum: Hardware
---

### Post by qazedci on 2009-02-01
Hello,

I just installed Ubuntu 8.04 on my M4400 with Quadro FX 770m. I have been having a lot of problems getting the display to work properly. So far I have probably spent 5 trying to fix this...

Anyways, I started out with 8.04 and tried to install drivers using a couple of methods. I tried to get drivers with envyng as shown in this post:

[http://ubuntuforums.org/showthread.php?p=5966495#post5966495](http://ubuntuforums.org/showthread.php?p=5966495#post5966495)

But that didn't work for me at all. I would still get an error saying that I was in low graphics mode or something. So I also tried getting the Linux driver directly from the Nvidia website and running that package from the terminal with a command like sudo sh Nvidiapackage.run. (I'm new to Linux...) That didn't really seem to do anything either. 

After trying each of those, I tried to access Nvidia settings with sudo nvidia-settings but it tells me to run sudo nvidia-xconfig as root and I do that. I get that to work and I restart, but when I run nvidia-settings again it tells me to do xconfig again. 

I then read that 8.10 might work better so I spend 1 hour upgrading to that and then stuff gets worse. My display has random artifacts at the top of the screen and another problem: My desktop's right half is on the left side of my screen and vice versa. Kind of hard to explain, but it was like the 'edge' of my screen was in the middle instead of the sides. 

Anyways, I downloaded envyng again and told it to uninstall my drivers. I restarted and then used envyng to install the second most recent drivers. This fixed the artifacts and the other problem but I am still in low graphics mode and my display and hardware is not recognized. 

**SHORT VERSION OF ABOVE: **I'm using a Dell Precision M4400 with Quadro FX 770M and Ubuntu 8.10. My screen is capable of 1920x1200 but I cannot set it above 1280x720. Ubuntu tells me that it is in low graphics mode despite my multiple attempts to install and configure different drivers. Here is the thread that I followed for a bit:

[http://ubuntuforums.org/showthread.php?p=5966495#post5966495](http://ubuntuforums.org/showthread.php?p=5966495#post5966495)

So could anyone help me get Nvidia drivers working on my laptop?

---

### Post by qazedci on 2009-02-03
bump

---

### Post by is2k on 2009-02-10
I have this notebook, though I'm thinking of returning it.

I installed the latest Nvidia drivers and was able to get my full resolution of 1920x1200.  My main problem with the notebook is that in Compiz, Flash performance is simply atrocious.  I get flickering and tearing constantly.  Switching back to Metacity (turning off advanced effects) and performance is considerably improved.

A second annoyance is the touchpad/trackpoint.  The touchpad loses sync (fills up my logs) and spazzes out, causing random clicks all over the screen.  It's completely unacceptable behavior.

---

