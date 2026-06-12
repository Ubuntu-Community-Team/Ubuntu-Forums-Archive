---
title: "[SOLVED] Compiz stopped working"
date: 2008-07-20
forum: General Help
---

### Post by slugicide on 2008-07-20
Hey all,
compiz stopped working and I can't figure out why.  I can't enable desktop effects as of yesterday.  The only clues I have are: the compiz-fusion splash screen doesn't start and the keyring manager no longer prompts me for a password at startup.  I'm using a Dell E1505 (and Hardy), so that means ATI.  Help me figure this out?  Thanks.

---

### Post by slugicide on 2008-07-20
No ideas?  I tried IRC, but it's always too busy there to get help.  I'd appreciate it.

---

### Post by Rocket2DMn on 2008-07-20
Can you please post the output of
```
lspci | grep VGA
compiz --replace
```

---

### Post by slugicide on 2008-07-21
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

---

### Post by Rocket2DMn on 2008-07-21
Are you running dual head?  Can you also please post your xorg.conf file?
```
cat /etc/X11/xorg.conf
```

How did you install the fgrlx drivers initially?  Did you recently get a kernel upgrade?

---

### Post by slugicide on 2008-07-21
Just a laptop.  Thanks for this.

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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
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

### Post by Rocket2DMn on 2008-07-21
That was fast, I still need to know how you originally installed the fglrx drivers.  From System->Administration->Hardware Drivers?  EnvyNG?  Manually?  It's also useful to know if you've had a kernel upgrade recently.

---

### Post by slugicide on 2008-07-21
Frankly, I don't remember how I installed it.  I think just through the restricted drivers option.  The last update to the kernel was last week, I think.

---

### Post by Rocket2DMn on 2008-07-21
Well, it sounds like something could be wrong with xorg's autodetection, in which case you can try reconfiguring X with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then restart X with CTRL+ALT+BACKSPACE.
Otherwise you may want to try reinstalling the fglrx drivers.  You can also try booting into an older kernel and seeing if the problem still exists.

---

### Post by slugicide on 2008-07-21
I tried everything you said and no change.  I'm currently running the previous kernel.  It still says "Desktop effects could not be enabled."

---

### Post by slugicide on 2008-07-22
bump

---

### Post by kidux on 2008-07-22
Try the script in [here]("http://ubuntuforums.org/showthread.php?t=799070") and see if it spits out any errors as to why it won't work.

---

### Post by slugicide on 2008-07-22
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility X1400
 Driver in use:         fglrx
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Another compositing manager in use. 

Would you like to know more? (Y/n) y

 The default window manager of GNOME has its own compositing manager to
 provide basic desktop effects.
 If this one is in use, Compiz will not be able to run. 

Do you want to disable GNOME's compositing manager? (Y/n) y
rodney@rodney-laptop:~$ !!
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility X1400
 Driver in use:         fglrx
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Fglrx driver not properly installed, you are using the Mesa driver. 


```

---

### Post by slugicide on 2008-07-22
That little script was all I needed to find out how to fix my problem.Thanks both of you!

---

### Post by kidux on 2008-07-22
Glad it worked, he did a great job on it, that's for sure.

---

