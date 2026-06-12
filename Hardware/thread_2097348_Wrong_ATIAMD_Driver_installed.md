---
title: "Wrong ATI/AMD Driver installed"
date: 2012-12-22
forum: Hardware
---

### Post by NBPX on 2012-12-22
I'm trying to run Amnesia: The Dark Descent demo from Steam, but it's too slow. Even with graphics in the minimum it's slow.

It's not a hardware problem because I can run Amnesia considerably well in Windows 7.

I took a look at Ubuntu Details Window. It says that my PC have as Graphics a VESA: RS880M. Catalyst says that it have a ATI Mobility Radeon HD 4200 Series.

The problem is that my computer have a ATI Mobility Radeon HD 5470.

The additional FGLRX drivers have been installed with Jockey.

I was using Ubuntu 12.10, but due the well known problems with video drivers I decided to install Ubuntu 12.04.

---

### Post by dannyboy79 on 2012-12-22
are you using compiz or 3d effects? I would suggest logging into a Gnome 2d session (without unity) and trying the game there. Check your top output when you fire up the game to see what's using all your memory.

---

### Post by 2F4U on 2012-12-22
Do you have a switchable graphics card? The user in this post

[http://ubuntuforums.org/showthread.php?t=2079757](http://ubuntuforums.org/showthread.php?t=2079757)

seems to have the same model. Can you provide the output of lspci | grep VGA?

---

### Post by v4mpiro on 2012-12-23
Hi, i have a notebook with the same gpus. Switching is not supported with catalyst drivers, so you will not be able to use your discrete card. 
Use Win7 to play, it's the only solution, or buy nvidia stuff. It's frustrating because now we could play on steam natively. :(

---

