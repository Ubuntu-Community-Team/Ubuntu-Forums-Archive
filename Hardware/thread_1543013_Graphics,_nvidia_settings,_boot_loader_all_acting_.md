---
title: "Graphics, nvidia settings, boot loader all acting up!"
date: 2010-07-31
forum: Hardware
---

### Post by banyanbraid on 2010-07-31
I have been having a world of problems ever since I installed Ubuntu 10.04. I originally ran Ubuntu through my Windows 7 folder using wubi. But I heard that there is less lag and stuff if Ubuntu is ran side by side in a separate hard drive partition. I was able to install and run Ubuntu and windows 7, but Ubuntu is really acting up. Here are the issues...

There are duplicate options of the same OS. Some of these work and some of these dont. For example, there is linux and a recovery linux option availabe, then a duplicate set of that that doesnt work, a windows 7 launcher that works, a windows 7 launcher that requires a product key, and a windows vista launcher that needs a product key. I have never even attempted to install windows vista so I dont know what that is doing there.

Now for the bigger problems:
1)after I attempt sudo method in the terminal, it proceeds to ask me for the password. But for some reason the keyboard wont let me type int he password.

2) I'm not able to change the appearance settings to enable extra visual effects. I really just wanted to do that so it would prompt me to install the nvidia proprietary drivers. My hardware drivers indicate that this driver is enabled but the following error message came up when I rebooted my system. 

Originally, I was able to enable the 3d effects with the compizconfig package. But I did not have all the options in that appearance manager as people in videos I'd seen. So I decided to reinstall the drivers, the compizconfig packages and the extra plugins for it in the hope that I could get all my 3d effects to work. 

None of this worked. Somebody please help me!!

---

### Post by banyanbraid on 2010-07-31
srry I forgot to post the error message i got upon reboot.

Ubuntu is running in low-graphics mode

1) Failed to initialize the nvidia kernel module
2)consult nvidia readme for details
3)******Aborting******
  Monitors found but none are usable

---

### Post by corrytonapple on 2010-07-31
For the graphics have you tried **System>Administration>Hardware Drivers**? When prompted for a password in terminal, you will not see it for security reasons. If you can wait, there are some people (including me) that are waiting for a tutorial to be posted. Here is where you can wait for the link:
[http://ubuntuforums.org/showthread.php?t=1538989&page=4](http://ubuntuforums.org/showthread.php?t=1538989&page=4)

---

### Post by oldfred on 2010-07-31
Sometimes BIOS settings on keyboard and mouse create problems. Check your BIOS settings. Windows it seems ignores the BIOS settings for USB keyboard so it may work even if the BIOS says it should only use the ps/2 ports.

---

