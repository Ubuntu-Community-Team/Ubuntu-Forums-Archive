---
title: "Monitor has no signal"
date: 2008-10-14
forum: General Help
---

### Post by Sonic011 on 2008-10-14
Hi, I just installed Ubuntu through Wubi and after I boot it, my moniter goes black and says no signal. I don't know if my drivers are corrupted or something but I would like to know how to fix this. I just re-installed the drivers on my current OS (Vista).

---

### Post by mikedep333 on 2008-10-14
Hey,
Some more info could be helpful. Could you tell us what graphics card (or laptop) you have?

Also, try hitting ctrl + alt + f1 after ubuntu loads. See if you can see the terminal (command-line interface.)

If that doesn't work, see if you can start ubuntu from rescue mode. To do this, select the rescue options from the grub menu (the black and white screen with the list of startup/linux kernel options.) If it is hidden, hit escape when it says the computer is about to start up with little white text on a black screen, and then select the rescue option. You may only have 3 seconds or so to hit escape, so be quick.

Also, later on if nothing works, you might want to try the version of ubuntu/wubi that is about to be released, the intrepid 8.10 release. It will have better hardware support. Here is a link to it:
[http://wubi-installer.org/devel/minefield/Wubi-8.10-rev510.exe](http://wubi-installer.org/devel/minefield/Wubi-8.10-rev510.exe)

---

### Post by Sonic011 on 2008-10-14
> **mikedep333 said:**
> Hey,
Some more info could be helpful. Could you tell us what graphics card (or laptop) you have?

Also, try hitting ctrl + alt + f1 after ubuntu loads. See if you can see the terminal (command-line interface.)

If that doesn't work, see if you can start ubuntu from rescue mode. To do this, select the rescue options from the grub menu (the black and white screen with the list of startup/linux kernel options.) If it is hidden, hit escape when it says the computer is about to start up with little white text on a black screen, and then select the rescue option. You may only have 3 seconds or so to hit escape, so be quick.

Also, later on if nothing works, you might want to try the version of ubuntu/wubi that is about to be released, the intrepid 8.10 release. It will have better hardware support. Here is a link to it:
[http://wubi-installer.org/devel/minefield/Wubi-8.10-rev510.exe](http://wubi-installer.org/devel/minefield/Wubi-8.10-rev510.exe)

Well it turns out it was my moniter drivers but I have a new problem, About half way when ubuntu loads it goes into a DOS screen and says "*ACTIVATING SWAPFILE SWAP..." and does nothing after that.

---

### Post by Sonic011 on 2008-10-14
Great, now I'm getting a new error saying no root file system is defined, please correct this from the partitioning menu

---

### Post by ago on 2008-10-15
[http://ubuntuforums.org/showthread.php?t=948083](http://ubuntuforums.org/showthread.php?t=948083)

---

