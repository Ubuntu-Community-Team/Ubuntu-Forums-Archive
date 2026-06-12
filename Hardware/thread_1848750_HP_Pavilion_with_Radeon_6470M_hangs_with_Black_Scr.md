---
title: "HP Pavilion with Radeon 6470M hangs with Black Screen on Boot"
date: 2011-09-23
forum: Hardware
---

### Post by GreekFreak on 2011-09-23
Hi,

I have recently purchased an HP Pavilion with a Radeon 6470M graphics card. I subsequently found out that this card is not yet supported for Ubuntu by ATI.

I followed the instructions of Post #2 in this thread ([http://ubuntuforums.org/showthread.php?t=1760264](http://ubuntuforums.org/showthread.php?t=1760264)) and installed the xorg-edgers ppa, which I think helped. I have not installed the ATI drivers, as every time I tried them the graphics were abysmal. I will wait for the version where my card is supported. 

However, there are times where when I boot that it hangs in a black screen. I have noticed that if it hangs, then the only way to get going is to boot with "nomodeset", and then restart, which seems to load the full graphics, using the generic drivers. This might simply be a coincidence (I haven't tried it enough times).

Is there anything I can do to stop this "hanging"

Thanks in advance for your help.

UPDATE: I have noticed that most times it hangs on the black screen and a few times it loads all the way. I'm assuming something conflicts, but I'm not sure what.

---

### Post by GreekFreak on 2011-09-24
bump...

---

### Post by GreekFreak on 2011-09-27
bump...

Has noone had a similar problem with an unsupported graphics card?

---

### Post by blastfm on 2011-09-27
Hello... I had the same issue. I basically had to blacklist the ATI card so Natty defaults to the Intel GPU instead. When I installed AMD Catalyst 11.8, i get a distorted(?) logon screen, which prevents me from logging in to the machine. So i uninstalled it and am currently using the Intel GPU.

I no longer experience the hang on startup after the blacklist thing. I'll try to look for where i found the workaround.

---

### Post by GreekFreak on 2011-09-27
> **blastfm said:**
> Hello... I had the same issue. I basically had to blacklist the ATI card so Natty defaults to the Intel GPU instead. When I installed AMD Catalyst 11.8, i get a distorted(?) logon screen, which prevents me from logging in to the machine. So i uninstalled it and am currently using the Intel GPU.

I no longer experience the hang on startup after the blacklist thing. I'll try to look for where i found the workaround.

I considered disabling the graphics card in BIOS, but that causes other problems (sometimes) with Ubuntu, as well as I'm dualbooting with Windows 7, so I'd rather not do that.

If you could let me know how (or the link) on how to blacklist the graphics card I'd greatly appreciate it.

---

### Post by dansk on 2012-02-10
Has anyone come up with a solution to this?  I'm experiencing the same occasional boot failure as the OP.  It's a nuisance more than anything, but it really would be nice if my laptop would boot successfully every time instead of only 1 in 4 times.

This happens with every flavour of Ubuntu - I'm currently using Lubuntu.  My laptop is a dv6-6195 with the Radeon HD 6700M.  I have it switched off using acpi_call.

---

### Post by Gregory Lee on 2012-02-10
I'm just now trying to install Ubuntu on an HP Pavilion desktop system p2-1220, with AMD APU A8-3820, integrated graphics ATI Radeon HD 6550D.  I haven't managed a successful install yet, and of course my hardware is not the same as yours, but who knows?  Maybe something I did will be a help.  I did have a black screen problem, and at least I got past that.

1. With my boot image burned to a DVD, I interrupted the HP boot sequence with the ESC key, and on HP's boot submenu, chose an option "legacy boot" from the DVD.  Why this should work while the default boot from DVD doesn't seem to, I have no idea.

2. When I got to the purple Grub(?) menu, I chose the "nomodeset" option with F6.

3. For Ubuntu 11.04, this only got me to a console typein shell, not the desktop.  However, I got better results booting Ubuntu 12.04 -- a nice graphical 2D desktop.  I'm using it now.  But no proper driver for 3D, yet.  I'm not ready to try for that, because ...

4. I can't install 12.04 yet.  After a half hour or so of working away at the install, it stops with the message "We're sorry, the installer crashed. ..."  I'm hoping that a more recent version of 12.04 will have fixed this problem.

5. By the way, I ran across a positive report (for Fedora 16) on the stability of the most recent version (12.01, I think) of Catalyst, AMD's proprietary ATI Linux driver, so my plan is to go for that, if I can't get a free driver to work for 3D graphics.

---

### Post by Gregory Lee on 2012-02-10
I did finally get 12.04 to install, by (1) using a hardwired ethernet connection instead of wireless, and (2) in the installation procedure unchecking the boxes for requesting proprietary drivers and for updating during the install.  I'm still booting up in the way I described previously, using the HP boot menu to ask for the DVD specifically and adding "nomodeset" to Grub's boot command.

(I'm not sure just what steps in what I did were important.  I'm just reporting facts, here.)

Now I'm ready to tackle finding a working 3D graphics driver.

Addendum: System Settings/Additional Drivers had an entry for activating the AMD fglrx proprietary driver, which I requested and restarted (as directed), so I guess I have the 3D driver, now.  That was easy.

---

### Post by dansk on 2012-02-10
Thanks for the posts, it sounds like your problems are a lot worse than what I'm dealing with.  I played around with adding nomodeset to grub a while back, and that did solve the black screen problem, but like you, it disabled any sort of advanced graphics capability.  Given the choice, I'd rather live with occasionally having to do a hard reset than giving up everything else.

It doesn't make sense to me that a computer can sporadically fail to boot for no apparent reason, but work perfectly fine the other 75% of the time...

---

### Post by Gregory Lee on 2012-02-11
> **dansk said:**
> ... but like you, it disabled any sort of advanced graphics capability. .
No, I have 3D graphics, now, since I installed the AMD proprietary graphics driver.  I no longer need to use nomodeset.  It works.

---

