---
title: "Can't install Nvidia driver! Using 2.6.24.3 costum kernel"
date: 2008-11-04
forum: General Help
---

### Post by utklasad on 2008-11-04
Greetings.

I'm kinda new to Linux, I've the Amilo XA 2528, the absolute negative Linux computer, maybe heard of it? Well, my computer don't work with any other Kernel than 2.6.24.3. [https://bugs.launchpad.net/ubuntu/+bug/189368](https://bugs.launchpad.net/ubuntu/+bug/189368) (if you are interested)

Here is the problem, a friend of mine gave me a working kernel for my computer (using hardy 8.04), I got headers and alsa packages. I installed them with dpkg -i. I rebooted, and everything seemed ok, DVD-drive was working, I had sound etc. Everything was nice, but, not my graphic card. I've tried to installed it in a lot of ways, nothing working. Nvidia manuel installation says something about kernel source, libc, cant identify my kernel source ~ or something like that.

sudo apt-get install nvidia-glx-new is not working either, I've also tried Envy, not working..

Ive tried to google this, but I don't find any solutions, so my question is: How do I make my Nvidia 8600m GS work for my custom kernel?

Remember, I'm new to this, so take it slow! :)

Kind Regards,
Blixmo

---

### Post by pedro_orange on 2008-11-04
Argh, don't install the driver from the nvidia website. I've had many problems caused by that!
(I'm sure alot of people have got it to work, but I never have properly)

First: sudo apt-get nvidia-glx-new is not a valid command!

You want: sudo apt-get install nvidia-glx-new

I personally installed my nvidia drivers using the restricted drivers manager under System > Administration > Restricted Drivers...

If none of these work, and you -have- to install the nvidia driver from the website. You'll need to fully post the output from the command so we can advise further.

Hope this helps

---

### Post by utklasad on 2008-11-04
Ah, I just wrote wrong, but I've tried sudo apt-get install nivdia-new-glx, I just get low-graphics mode and nothing happends, and the restricted drive manager is just empty, or I cant find anything saying "restricted drive manager" but I have Hardware drivers, same?. But if I boot with the original kernel it works. But then nothing else works, heh, I need this kernel..

Well, I will take a look at it again, thanks for reply!

---

### Post by pedro_orange on 2008-11-04
Yes Hardware Drivers should list the propriety drivers on your system.

It may well be in there, but it may be not.

What happened when you entered the command? Package not found?

You can use apt-cache search package-name to search for packages before u attempt to download.
Perhaps you need to add a repo or something.

With regards to installing the driver from the website, I'd just read and follow the instructions carefully and then you usually can't go wrong.

Good luck

---

### Post by utklasad on 2008-11-04
I used sudo apt-get install nivdia-glx-new . 1 new package installed, reboot and it seems to work, its a little bit smoother and nicer resolution, but when i run glxgears I get this in terminal: 

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

edit:

In Hardware Drivers I have:

Intel HDA Driver - In use
PC Speaker Driver - In use

Thats all, no graphic card, but as I said, if I boot original kernel I have my card there, and it works nice, strange? Well, I have to get it to work with this kernel. Thanks for help this far!

---

### Post by pedro_orange on 2008-11-04
Ah right so you have no glx it seems?
What does:

```
glxinfo
```

say?

What driver does it say you're using in your /etc/X11/xorg.conf ?
Also check out your /var/log/Xorg.0.log for hints!

AH! So it works in the old kernel? 
Stick a copy of your xorg.conf on a flash drive from the one that works.
Then boot into the other kernel and compare the two xorg.confs for differences.

---

### Post by utklasad on 2008-11-04
_glxinfo:_

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x49 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

[U]xorg.conf:
[/U]

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"sv"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection




I'm checking Xorg log right now, but as I said, I'm kinda new to this, but I know alot about computers etc. So I will check this log for some minutes to, to long to be posted :p

Well, the only thing that works in the other "newer" kernel is the graphic card, this "older" kernel my friend compiled for me makes everything else work. Everything I wrote now was from this kernel I'm using. 2.6.24.3 Costum Kernel - Amilo XA 2528

---

### Post by pedro_orange on 2008-11-04
Ok you xorg.conf doesn't actually specify which driver you're using for your graphics. It should be under the 'Device' heading. As you can see it only says:

Section "Device"
Identifier "Configured Video Device"
EndSection

Which tells us nothing really.

You should boot up into the kernel that has your graphics card actually working and sneak a look at the xorg.conf there.
For example mine says:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

I wouldn't copy and paste this into yours though, as it may not have the nvidia driver installed.

If you xorg.conf on the working graphical kernel doesn't have any mention of the driver then if I remember correctly you can specify which driver you wish to use by doing a:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

From memory, I think you have to be in another desktop thats not running xserver to get this going. (Ctrl+Alt+F2) 

This process doesn't take a long time, but it does as you alot of questions. I would say if you're unsure as to what to choose, just choose what it has highlighted as default.

Good luck

---

### Post by utklasad on 2008-11-05
Thanks so much for all help, but still not working. I managed to start the original kernel, and copied that xorg into this kernel,

my device now:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection


Ive changed all that into same as my working graphical kernel, still is my computer running in low-graphics mode with the compiled kernel, and glxgears still not working.. Strange strange

---

### Post by utklasad on 2008-11-05
Here is my xorg.conf as it is now, looking kinda exact as the working graphical kernel

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"sv"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by utklasad on 2008-11-07
Bump bump ~ would love some help to solve this!

---

### Post by utklasad on 2008-11-09
Bump bump ~ would love some help to solve this!

---

