---
title: "Urgent help needed."
date: 2008-07-21
forum: Hardware
---

### Post by mirchichamu on 2008-07-21
Recently I have to reinstall Ubuntu because of my mistake. Before it was working well but now after re installation, I am having problem with screen resolution. It is only showing 800 * 640 only. I need help how to resolve this issue. 

My laptop specs: Fujitsu-Siemens amilo 1470. 1.7 centrino, 512 RAM , 80 GB
Graphics: ATI mobility Radeon.

---

### Post by eldirr on 2008-07-21
Which driver did you install?  And can you add your xorg.conf file,'fglrxinfo' output too?

(xorg.conf file path = /etc/X11/xorg.conf )

---

### Post by mirchichamu on 2008-07-21
> **eldirr said:**
> Which driver did you install?  And can you add your xorg.conf file,'fglrxinfo' output too?


Thanks for support.
Please see this output file.

---

### Post by mbsullivan on 2008-07-21
Could we get the contents of your /etc/X11/xorg.conf file as well? Attaching the file as an attachment would work.

Mike

---

### Post by eldirr on 2008-07-21
It looks like you didn't install any ATI driver (we can be sure after seeing your xorg.conf file) 

You can try theese; 

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) (method1, method2)

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers)

[http://itcertforum.com/forum/showthread.php?t=197](http://itcertforum.com/forum/showthread.php?t=197)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

(I don't know if it works but it would be better if you take a backup of your xorg.conf file before doing these stuff) 

*If your system crash after trying theese you can press 'ESC' when the it asks while booting, and choose recovery mode. Then enter the root and edit your xorg.conf file again with the video device driver as 'vesa'. It will open again at 640x480 or 800x600 *

---

### Post by mirchichamu on 2008-07-21
> **mbsullivan said:**
> Could we get the contents of your /etc/X11/xorg.conf file as well? Attaching the file as an attachment would work.

Mike

Thanks mbsullivan for support.
I got a reply that permission denied.

---

### Post by mirchichamu on 2008-07-21
> **eldirr said:**
> It looks like you didn't install any ATI driver (we can be sure after seeing your xorg.conf file) 

You can try theese; 

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) (method1, method2)

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers)

[http://itcertforum.com/forum/showthread.php?t=197](http://itcertforum.com/forum/showthread.php?t=197)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

(I don't know if it works but it would be better if you take a backup of your xorg.conf file before doing these stuff) 

*If your system crash after trying theese you can press 'ESC' when the it asks while booting, and choose recovery mode. Then enter the root and edit your xorg.conf file again with the video device driver as 'vesa'. It will open again at 640x480 or 800x600 *

Sorry sir! Thanks for your support but I am not computer professional. Please tell some simple steps to correct this.

---

### Post by mirchichamu on 2008-07-21
I started my laptop in recvery mode and then x-fix but unfortunately although the resolution was ok, the display froze at log on. I shut down my laptop through shut down button and restarted but again froze. What to do next???

---

### Post by mbsullivan on 2008-07-21
> I started my laptop in recvery mode and then x-fix but unfortunately although the resolution was ok, the display froze at log on. I shut down my laptop through shut down button and restarted but again froze. What to do next???

Just for now, try (as eldirr suggested) using the "vesa" drivers for your graphics card. This will prevent your GPU from doing any hardware accelerated 2D graphics processing, and instead do it all in software (on the CPU). It is slower than the alternative, but will avoid any driver nastiness (which appears to be what you are experiencing).

To do this, you will need to edit your /etc/X11/xorg.conf file. The reason you are getting "permission" errors when you access this file is that it is owned by root, and you are a normal user. In order to access it, you will need to precede any command with "sudo" for "super user do". Thus, to edit xorg.conf in gedit (notepad replacement), give the following a try:

```
sudo gedit /etc/X11/xorg.conf
```

Then locate the section that starts with something like the following:

```
Section "Device"
	Identifier	"Radeon-Single"
	Driver		"ati"

```

And change the "Driver" to "vesa":

```
Section "Device"
	Identifier	"Radeon-Single"
	Driver		"vesa"

```

It would also be useful to copy your xorg.conf file and set the permissions so that you can upload it to these forums:

```
sudo -s
cp /etc/X11/xorg.conf /tmp
chmod 755 /tmp/xorg.conf
[upload /tmp/xorg.conf]
```

Sorry for all the terminal commands... I don't have regular Ubuntu installed and it's easier to send text commands through the forum.

Hope this helps!
Mike

PS: 

You could also try using the proprietary fglrx graphics drivers released by ATI, instead of their free counterparts (the proprietary ones tend to work slightly better on newer cards). We're not 100% sure what drivers you're using right now (without an xorg.conf to look at), but I think it's reasonable to guess that Ubuntu detected the presence of an ATI card, and defaulted to the free ATI drivers.

I don't have an ATI card, so I don't know, but it seems to me (from [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")) that the following should enable the fglrx drivers:

(1) Install the drivers:

```
sudo aptitude install linux-restricted-modules-generic restricted-manager
```

(2) Enable the new drivers:

Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver" (taken directly)

(3) Insert kernel module:

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

(4) Reboot.

---

### Post by mirchichamu on 2008-07-22
Thanks mbsullivan for your interest to help me. Kindly look at this post.
[http://ubuntuforums.org/showthread.php?p=5435426#post5435426](http://ubuntuforums.org/showthread.php?p=5435426#post5435426)

---

### Post by mbsullivan on 2008-07-22
Have you tried switching the video driver in xorg.conf to "vesa" (as in my post above)? Since you can't start X, you can use a text-only editor (such as "nano" or "pico") from the recovery console.

Then try booting fully. Best case scenario it **won't** be full resolution, yet, but at least then we can do some more serious work. Afterwards, could you post your xorg.conf file (using the instructions from above)?

```
sudo -s
cp /etc/X11/xorg.conf /tmp
chmod 755 /tmp/xorg.conf
[upload /tmp/xorg.conf]
```

Also, check for any backups (as was suggested in the other forum thread). Post the output of:

```
ls /etc/X11/ | grep xorg
```

Mike

---

### Post by mirchichamu on 2008-07-22
> **mbsullivan said:**
> Just for now, try (as eldirr suggested) using the "vesa" drivers for your graphics card. This will prevent your GPU from doing any hardware accelerated 2D graphics processing, and instead do it all in software (on the CPU). It is slower than the alternative, but will avoid any driver nastiness (which appears to be what you are experiencing).

To do this, you will need to edit your /etc/X11/xorg.conf file. The reason you are getting "permission" errors when you access this file is that it is owned by root, and you are a normal user. In order to access it, you will need to precede any command with "sudo" for "super user do". Thus, to edit xorg.conf in gedit (notepad replacement), give the following a try:

```
sudo gedit /etc/X11/xorg.conf
```

Then locate the section that starts with something like the following:

```
Section "Device"
	Identifier	"Radeon-Single"
	Driver		"ati"

```

And change the "Driver" to "vesa":

```
Section "Device"
	Identifier	"Radeon-Single"
	Driver		"vesa"

```

It would also be useful to copy your xorg.conf file and set the permissions so that you can upload it to these forums:

```
sudo -s
cp /etc/X11/xorg.conf /tmp
chmod 755 /tmp/xorg.conf
[upload /tmp/xorg.conf]
```

Sorry for all the terminal commands... I don't have regular Ubuntu installed and it's easier to send text commands through the forum.

Hope this helps!
Mike

PS: 

You could also try using the proprietary fglrx graphics drivers released by ATI, instead of their free counterparts (the proprietary ones tend to work slightly better on newer cards). We're not 100% sure what drivers you're using right now (without an xorg.conf to look at), but I think it's reasonable to guess that Ubuntu detected the presence of an ATI card, and defaulted to the free ATI drivers.

I don't have an ATI card, so I don't know, but it seems to me (from [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")) that the following should enable the fglrx drivers:

(1) Install the drivers:

```
sudo aptitude install linux-restricted-modules-generic restricted-manager
```

(2) Enable the new drivers:

Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver" (taken directly)

(3) Insert kernel module:

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

(4) Reboot.

Thanks a lot. I got this:
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
	Option		"XkbLayout"	"us"
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
	Driver		"vesa"
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

---

### Post by mirchichamu on 2008-07-22
Dear all!
It gave me very painful experience. I had to remove grubb and ubuntu partitions and tried to install fresh ubuntu. But unnfortunately after doing all these, it failed once again. Only I was able to install again in low graphics mode. My display is only 800 * 600. Very ugly looking. I am fed up really.

---

### Post by mirchichamu on 2008-07-22
Ultimately after long fighting I am able to install the restricted driver, but there is icon of restricted driver on the panel. I don't know what will happen when I restart my laptop?
My display is now ok.

---

### Post by eldirr on 2008-07-22
ATI released a new version driver last night(it says it supports Ubuntu 8.04 now), i will try this and will tell you if it works. 

Don't give up the fight :D

---

### Post by mirchichamu on 2008-07-22
> **eldirr said:**
> ATI released a new version driver last night(it says it supports Ubuntu 8.04 now), i will try this and will tell you if it works. 

Don't give up the fight :D

I shall be much thankful, if you worked out.

---

### Post by mbsullivan on 2008-07-22
> 
Ultimately after long fighting I am able to install the restricted driver, but there is icon of restricted driver on the panel. I don't know what will happen when I restart my laptop?
My display is now ok.

Have you restarted, yet? I wonder what will happen :???: Graphics issues are some of the most painful in Linux, due in no small part to the peculiarities of X and also the non-free and disparate natures of all the GPUs available.

The situation may slowly be getting better, though... Intel released documents about their graphics cards, and AMD/ATI is slowly coming around, too. NVidia is still the bad guy in this race, I'm afraid.

Mike

---

### Post by mirchichamu on 2008-07-24
> **mbsullivan said:**
> Have you restarted, yet? I wonder what will happen :???: Graphics issues are some of the most painful in Linux, due in no small part to the peculiarities of X and also the non-free and disparate natures of all the GPUs available.

The situation may slowly be getting better, though... Intel released documents about their graphics cards, and AMD/ATI is slowly coming around, too. NVidia is still the bad guy in this race, I'm afraid.

Mike

Thanks mbsullivan for being with me all the time.
Very painful situation. As I mentioned of my fear, when I restarted, I got a blank screen after log on. Then I left my laptop,it is useless. I don't know for how long I will suffer this. I am with you from my desktop now.

---

### Post by mbsullivan on 2008-07-25
> Very painful situation. As I mentioned of my fear, when I restarted, I got a blank screen after log on. Then I left my laptop,it is useless. I don't know for how long I will suffer this. I am with you from my desktop now.

This sure is turning into a nightmare! If you boot to the recovery console and look at your xorg.conf file again, what do you see when you originally had:

```
Section "Device"
Identifier "Configured Video Device"
Driver     "vesa"
EndSection
```

???

I think it should look more like:

```
Section "Device"
Identifier "Configured Video Device"
Driver		"fglrx"
Option		"VideoOverlay"	"on"
Option		"OpenGLOverlay"	"off"
EndSection
```

You could try modifying it with a command-line text editor and restarting, if it is different.

Also, what "vendor" string do you get from the output of:

```
fglrxinfo
```

???

Mike

---

