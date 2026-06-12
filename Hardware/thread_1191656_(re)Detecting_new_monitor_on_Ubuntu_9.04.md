---
title: "(re)Detecting new monitor on Ubuntu 9.04"
date: 2009-06-19
forum: Hardware
---

### Post by peroa on 2009-06-19
I would like to ask one question.

I had to change monitors on my Ubuntu system and now not all resolutions are working.

Is there a "how to" on this problem?

I found "dpkg-reconfigure xserver-xorg" but there I only get options for my keyboard redetection.

Could anybody please help me, it`s quite urgent!
:(

---

### Post by peroa on 2009-06-19
No ideas?

---

### Post by jeporcher on 2009-07-17
I have the same problem, only it's not redetection I want, just plain detection. I installed Ubuntu yesterday on my PC but it doesn't detect my monitor and I can't configure it up to optimum resolution, which is just 1280x1024 (not a lot to ask!).

I'd appreciate some help on this, which I found to be Ubuntu's weakest point so far for a beginner (I tried to no avail rewriting xorg.conf based on some random posts I found, and "dpkg-reconfigure xserver-xorg" only gives me options for keyboard redetection too).

---

### Post by James- on 2009-07-17
first backup your xorg.conf

in terminal:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
then

```

sudo gedit /etc/X11/xorg.conf

```

under the  section screen there should be a section "display" kinda  like this:
```

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

```

Add a "Modes" line in the display section:

```

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
                Modes       "1280x1024" "1024x768"
	EndSubSection
EndSection

```

make sure your monitor can handle that sort of resolution

if anything goes wrong  when you reboot press ctrl+alt+f1
login and type you will have to reboot or if you have dontzap return to GUI by pressing ctrl+alt+f7 then press ctrl+alt+bkspc

```

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```

now reboot(or ctrl+alt+bkspc if you have dontzap) and you should have the resolutions available to you

---

