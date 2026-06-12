---
title: "[SOLVED] Hardy - recent kernel update wiped out nvidia closed driver"
date: 2008-07-16
forum: General Help
---

### Post by Jose Catre-Vandis on 2008-07-16
Hi

The kernel upgrade I did last night -> to 26.19 completely borked my nvidia driver /xserver settings. On reboot it forced me into low graphics mode.

I rebooted into recovery mode and was able to fix xorg.conf, so that I could at least boot into a usable resolution, however, all compiz desktop effects have gone and cannot enable them through "Appearance". Also, looking in "Hardware Drivers" it appears I have no restricted driver installed (it was, on installation and setup of hardy in the first place). Synaptic tells me I am running on nvidia-glx-new. I use an Nvidia 6800 card.

Can anyone tell me how to get the restricted driver installed again (preferably through the ubuntu way, not from source) and I guess this will then allow desktop effects to be restored?

btw, the kernel upgrade also appeared for a short while to wipe my Firefox 3 profile, but after a few tries it all came back.

First problems I have had with hardy, which otherwise has been super solid and reliable.

Thanks

Jose

---

### Post by arkara on 2008-07-16
Yes this is normal.
It is caused by the kernel change, because the nvidia module compiled by the nvidia-glx package, is based only in your previous kernel.
what you could do, is

open a terminal, then become root user by typing

```
 sudo su 
``` 

and then type.

```
apt-get remove nvidia-glx && apt-get install nvidia-glx
```

---

### Post by Jose Catre-Vandis on 2008-07-16
Thanks arkara. I presume you mean nvidia-glx-new?

I ran this command```
apt-get remove nvidia-glx-new && apt-get install nvidia-glx-new
``` and then rebooted. No change to desktop resolution (1280x1024) but still not able to enable desktop effects, and no restricted driver shown in hardware drivers. So still missing something somewhere?

---

### Post by arkara on 2008-07-16
> **Jose Catre-Vandis said:**
> Thanks arkara. I presume you mean nvidia-glx-new?

I ran this command```
apt-get remove nvidia-glx-new && apt-get install nvidia-glx-new
``` and then rebooted. No change to desktop resolution (1280x1024) but still not able to enable desktop effects, and no restricted driver shown in hardware drivers. So still missing something somewhere?

if the package is nvidia-glx or nvidia-glx-new depends on the model of your nvidia card..
do a search on the ubuntu packages page for both of the packages.
Hopefully it will say the models of supported cards..and so you must reinstall the package that corresponds to your card..

where are you? on ubuntu or kubuntu?

---

### Post by drs305 on 2008-07-16
Try installing and running EnvyNG to reinstall your driver.
```
sudo aptitude install envyng-gtk
```

Run with System Tools > EnvyNG

There will also be System, Admin, Nvidia X Configuration and 'gksu nvidia-settings'

---

### Post by Jose Catre-Vandis on 2008-07-16
Have tried nvidia-glx and nvidia-glx-new. both give me a good resolution, but no compix and nothing in "Hardware Drivers"

Will try Nvidia Settings and then Envy next :)

Nvidia Settings won't run because of the "plug and play" setup of xorg.conf

---

### Post by jocko on 2008-07-16
Make sure you have the restricted-modules package for the latest kernel installed, otherwise you'll never get the nvidia drivers to work.
An easy way to make sure you always have restricted-modules matching your kernel is to install the metapackage "linux" (which in turn depends on the metapackages "linux-image" and "linux-restricted-modules", which depends on... you get the point...).
Note that this will prevent a kernel update until there is an updated restricted-modules package available, making sure you don't break your drivers by updating just the kernel.

**EDIT**: Apparently the last kernel update was not different enough from the old kernel to require an update of the restricted modules, so that's not the problem.
The nvidia driver works fine for me after the update... so you can probably disregard my post...

---

### Post by Jose Catre-Vandis on 2008-07-16
OK running Envy did the trick and am now back running compiz. However, my mozilla firefox profile has gone doolally again, so hopefully it will come back soon.

jocko, thanks for the info regarding restricted packages. Odd we have to do this to overcome the effects of a kernel upgrade, and it is not taken care of by the update process

---

### Post by bodhi.zazen on 2008-07-16
If you have nvidia-glx or nvidia-glx-new installed, try configuring with nvidia-settings (you may need to install nvidia-settings first).

```
gksu nvidia-settings
```

If you like the resolution you ge, save changes :)

If that fails, you can try envy, but you need to remove nvidis-glx and nvidia-glx-new first.

With kernel upgrades, you need to re-install the propriatry driver each time (happens automatically with nvidia-glx and nvidial-glx-new).

---

### Post by Jose Catre-Vandis on 2008-07-16
I believe I had nvidia-glx-new before the update so am somewhat bemused about the whole thing.

I'm going back to Windows, this sort of thing never happens there :lol:
(please this is a joke :))

---

### Post by Cone on 2008-07-16
> **Jose Catre-Vandis said:**
> However, my mozilla firefox profile has gone doolally again, so hopefully it will come back soon.


Are you logged in as root (something you shouldn't do, by the way) and thus running Firefox as root?  I've never seen any problems with firefox profiles disappearing.

o___O

---

### Post by bodhi.zazen on 2008-07-16
That has happened to me infrequently (with kernel updates, usually on encrypted systems)

Re-install the kernel and/or nvidia-glx-new ~ worked for me.

---

### Post by Jose Catre-Vandis on 2008-07-16
Ah, the risks of multitasking! I had filled up my home/filesystem partition, with 0 bytes available. This meant that firefox couldn't load up what it needed, I had a clear out and Firefox is back to doing what it does best.

Thanks to everyone for their help and advice. I'll mark as solved.

Oh, and ironically, the joke is on me (see earlier in thread)...what filled up the partition, a partial install of Windows in Virtualbox! :lol:

---

### Post by Huss on 2008-07-16
From a noob to other noobs ...

To get my Nvidia 6 series working I had to:

- Make sure the boot loader used the updated kernel (I selected "use existing menu.lst" after update - oops)
- Get the restricted drivers for the new kernel
- Install and run envy (works well with auto detect) 
- Then enable 3d effects in system ->preferences->appearance ->visualeffects
- and finally tweak the resolution with the screens and settings app

---

### Post by ffahog on 2008-07-18
I have the same problem described in the beginning of this thread. I upgraded from 7.10 to 8.04 a few weeks ago and have been living with the consequences since. After trying the solutions presented here, I am still in need of some help.

When I used the terminal to remove and reinstall the nvidia driver, I ended up with a usable screen resolution; however, there were still some problems. For example, anything utilizing accelerated graphics or 3d effects do not work. It is clear that all is not well.

(Also, there are a couple of odd side effects: For example, I believe the computer is having trouble detecting my monitor(?), and because of this I cannot run 'gksudo nautilus' to edit files and directories as a root user. Another weird side effect is that my log-in screen shows only about 60% of the screen, and when I try to "scroll" around the unseen portions of my screen with the mouse, it doesn't work.)

Now, as for the solutions. Envy doesn't appear to work for me. Whereas manually removing and installing nvidia-glx results in what I've described above, removing the driver (manually or with Envy) and reinstalling it with Envy results in the same 'low graphics mode' problem. I've tried different combinations of uninstalling, installing, restarting, and doing it manually and with Envy&#8212;none seem to work.

What's interesting is that I'm using Ubuntu with another hard drive (40gb) on this same computer. On my second hard drive, I installed 7.10 but immediately upgraded to 8.04, after which I installed the nvidia driver without a breeze. So I know that it can work in principle. It's just that my upgrade to the new kernel on THIS hard drive screwed with it, and I can't figure out the right steps to solve the problem.

Is there anyone that can help? I'd greatly appreciate it!

---

### Post by Jose Catre-Vandis on 2008-07-19
What's your grpahics card, and what does your xorg.conf look like ```
cat /etc/X11/xorg.conf
``` Here is mine after success with Envy > Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
 

Worth looking at your xorg.conf in your working Ubuntu to check differences

---

### Post by Jose Catre-Vandis on 2008-07-27
Interestingly, I see that a few updates later, the proprietory drivers are back in the Hardware section, waiting to be installed. After all that stuff with Envy, do I go back or forward?  :) I have a few glitches with window title bars currently with envy and compiz

---

### Post by Lakjin on 2008-07-29
The same thing happened to me but I have an ATI card.
Envy doesnt seem to work properly for me, cant enable compiz, scrolling is choppy etc.

Still searching for a fix.

---

### Post by markbuntu on 2008-07-29
> **Lakjin said:**
> The same thing happened to me but I have an ATI card.
Envy doesnt seem to work properly for me, cant enable compiz, scrolling is choppy etc.

Still searching for a fix.

If you updated to the -20 kernel and are using the ati driver fglrx 8.5 or newer that you got from ati, the kernel did not know what to do with the fglrx kernel modules so it left them out of the build. You can install them by running this command from wherever you put the debs:

sudo dpkg -i fglrx-kernel-source_*.deb

Alternatively, you can download the driver again and dpkg it and then run the command.

Don't forget to reboot.

---

