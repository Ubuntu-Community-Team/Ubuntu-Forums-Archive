---
title: "How do you dual boot 2 OS from 2 hard drives?"
date: 2010-08-14
forum: Hardware
---

### Post by garycheng12 on 2010-08-14
Before someone posts a guide to dual booting, this problem is different (or at least I think it is). What I am trying to do is: 

- Set up a menu (a boot loader?) to be able to select which OS, 
Windows 7 or Ubuntu, to boot. 

The problem for me: 

- I have Windows 7 installed in an internal hard drive in the 
computer. 
- I have Ubuntu 10.04 (32-bit) installed in a partition of an external hard drive.


What I currently am doing is: 

After installing Ubuntu on the external hard drive, I am able to run it without problems. If I were to unplug the external hard drive and restart the computer, the computer would boot into Windows 7 automatically, which is normal. If I plugged in the hard drive and then restarted the computer, it would automatically boot Ubuntu, which is what it should do. However, how can I set up the boot loader such that I am able to SELECT which OS to boot if I had my external hard drive plugged in? It will boot into Windows 7 automatically if the user does not select an OS after 5 seconds. If external hard drive was not plugged in, then it will boot into Windows automatically. I don't know if GRUB has anything to do with this (I have never played with dual booting nor boot loaders before), then I prefer to use GRUB 2 as it seems to have significant advantages over the older version (I generally prefer using up-to-date applications as they almost always contain speed/security improvements). 


I know that Startup Manager can tweak the GRUB and customize it to my likings, but how can I actually setup GRUB to perform the task above?

Thanks, guys.

---

### Post by J_Boner on 2010-08-14
Not quite sure if menu.lst has been removed from ubuntu 10.04 or not, I am only running a single boot system. Anyway try this:

terminal: sudo gedit /boot/grub/menu.lst

if menu.lst exists in your system, you are looking for this:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

If it looks like that make it look like this:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

hope it helps, J_Boner

---

### Post by S.R on 2010-08-14
GRUB2 use grub.cfg ... Guessing you have GRUB installed on the external?

---

### Post by oldfred on 2010-08-14
I would think Startup manager would do what you want but if you want to totally customize grub:

Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom - Similar to post above:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and copied entries inot 40_custom & then totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---

### Post by garycheng12 on 2010-08-14
I don't even have GRUB installed O_O. How and where should I install it? I have never even played with the terminal yet, so I don't really have a clue what you guys are talking about =/, sorry.

---

### Post by cariboo on 2010-08-14
Boot into your Ubuntu installation, and once at the desktop, open an terminal and install grub:

```
sudo grub-install /dev/sdX
```

Where /dev/sdX is your extenal drive. Once grub is installed, type:

```
sudo update-grub
```

grub should detect all the operating systems you have installed. you will see a listing as the the operating systems are detected.

Reboot and your done.

There is nothing magical about grub2, it just plain works. I have a system with XP, Kubuntu 10.10, Ubuntu 10.10, PCLinuxOS 2010 and XMBC installed, grub2 finds all of them with no problems.

PCLinoxOS still uses grub-legacy, which has to be hand edited every time you install another os, or even upgrade kernels, so I don't use it.

---

### Post by cariboo on 2010-08-14
Boot into your Ubuntu installation, and once at the desktop, open an terminal and install grub:

```
sudo grub-install /dev/sdX
```

Where /dev/sdX is your extenal drive. Once grub is installed, type:

```
sudo update-grub
```

grub should detect all the operating systems you have installed. you will see a listing as the the operating systems are detected.

Reboot and your done.

**Note** Using this method doesn't make any changes to your Windows mbr, so when the external drive is disconnected Windows will boot normally.

There is nothing magical about grub2, it just plain works. I have a system with XP, Kubuntu 10.10, Ubuntu 10.10, PCLinuxOS 2010 and XMBC installed, grub2 finds all of them with no problems.

PCLinoxOS still uses grub-legacy, which has to be hand edited every time you install another os, or even upgrade kernels, so I don't use it.

---

### Post by S.R on 2010-08-17
One recommendation I have is to remove your laptop internal HDD unless you are absolutely positive you know what you are doing. Plus if you install GRUB on the external you should be able to plug in to any other computer and run your external. At least that has been my experience.

Only suggest so you are operating as safely as possible when you install GRUB ...

---

