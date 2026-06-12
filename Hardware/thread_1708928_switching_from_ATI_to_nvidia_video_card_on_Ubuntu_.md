---
title: "switching from ATI to nvidia video card on Ubuntu 10.10"
date: 2011-03-17
forum: Hardware
---

### Post by rvboutin on 2011-03-17
Hi all,
I am new in using Linux and Ubuntu so, although I have been googling for it, I need a bit of help.
I use my work PC with a Dual boot Windows XP / Ubuntu 10.10.
To be able to run some application I am upgrading my video card from ATI 2400 Pro (256Mb RAM) to a Palit GeForce 8400GS Super (512Mb RAM). As I have only a PCIe x16 port, my option were limited.
My question is:
What are the critical steps before or after swapping the card to avoid messing up my install of Ubuntu 10.10 (I emphasize 10.10 because most of the post I have found refers to old version of Ubuntu (~7 to 9) and not Maverick).
I have spent a substantial amount of time installing and configuring my image analysis software so I do not want to have to go through a reinstall.
Although, as a newbie I am not very good at being stuck with a meaningless minimal console after rebooting :D
Thanks in advance for your help :popcorn:
Cheers,
Rv

---

### Post by DanneStrat on 2011-03-17
Deleted post

---

### Post by rvboutin on 2011-03-24
Hi,
DanneStrat replied: "There should not be any need to take any precautions
before swapping to another card. The module for your
old video card should unload automatically and a new
one will be loaded for your new card.
Just make sure you power down the computer completely
(not suspending or hibernating) before proceeding
with the swap."
He has deleted his post, maybe because that did not work as planned.. #-o
I had to go through: sudo apt-get remove fglrx (see here: [http://ubuntuforums.org/showthread.php?t=517225](http://ubuntuforums.org/showthread.php?t=517225)) and then restart in recovery mode and chose to start with the basic display.
I was then able to install the nvidia driver for my new card.
Hope that help others.
Cheers,
Rv

---

### Post by DanneStrat on 2011-03-24
> **rvboutin said:**
> Hi,
DanneStrat replied: "There should not be any need to take any precautions
before swapping to another card. The module for your
old video card should unload automatically and a new
one will be loaded for your new card.
Just make sure you power down the computer completely
(not suspending or hibernating) before proceeding
with the swap."
He has deleted his post, maybe because that did not work as planned.. #-o
I had to go through: sudo apt-get remove fglrx (see here: [http://ubuntuforums.org/showthread.php?t=517225](http://ubuntuforums.org/showthread.php?t=517225)) and then restart in recovery mode and chose to start with the basic display.
I was then able to install the nvidia driver for my new card.
Hope that help others.
Cheers,
Rv

Exactly, I realized that my instructions would only

work when swapping between two cards of the same brand so

I deleted the post and forgot to reply back with the

correct instructions.

Glad you got it working!

---

### Post by Hippytaff on 2011-03-24
Nvidia can be fun :-) but the [Canonical component catalog]("http://www.ubuntu.com/certification/catalog") is always worth a look before buying hardware that you want to use with ubuntu

---

### Post by rvboutin on 2011-03-25
Hi,
OK thanks for your reply, but sorry that does not help me much. Searching the website I could not find many nvidia video card in there, does this mean that they are not compatible with Ubuuntu?
If that's the case, that's rubbish really!
Cheers,
Rv

---

### Post by realzippy on 2011-03-25
The 8400 GS should work.
If you have not installed a driver (catalyst/fglrx) for your old ATI card formerly,you not need to prepare the system for anything,just change cards,reboot,
After reboot you can install the nvidia driver,until you do so,the free nouveau driver will "drive" your card.

---

### Post by rvboutin on 2011-03-25
OK thanks for your answer.
I got it working fine after uninstalling the nvidia driver completely and reinstalling it.
I now have dual display working, however I got a message at each login saying "Could not apply the stored configuration for monitors
X Server does not support size requested" although everything seems to work fine.
Shall I just ignore that warning? Is it just a bug in nvidia drivers? I had no problem whatsoever with my ATI card.
Cheers,
Rv

---

### Post by realzippy on 2011-03-25
...maybe there is an old file "monitors.xml" left.
Delete it :

```
rm ~/.config/monitors.xml
```

Make your settings with nvidia-settings,not with the
System/Settings/Monitors tool.

---

