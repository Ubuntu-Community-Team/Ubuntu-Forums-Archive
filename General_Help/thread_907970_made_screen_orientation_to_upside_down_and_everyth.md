---
title: "made screen orientation to upside down and everything broke"
date: 2008-09-02
forum: General Help
---

### Post by brnetonboy on 2008-09-02
i was changing my screen resolution and i put the orientation to upside down--then everything became unresponsive, so i ctrl+alt+backspaced, but when i logged in again nothing showed up except my upside-down cursor.

is there a way to change the resolution back to right-side up while logged in as another user?

also, i tried to log in as "root" but it wouldn't let me...

---

### Post by keplerspeed on 2008-09-02
Hi,

If you boot into recovery mode, you can reset your xorg.conf file, of which contains the x server configurations. When booting into recovery, a menu should appear, allowing you to select to reset xorg, called 'xfix'.

Otherwise boot normaly, and drop to root shell by pressing ctrl-alt-f1 or f2, or after booting in recovery mode select to drop into root shell, then use vi to look at your xorg.conf file:

sudo vi /etc/X11/xorg.conf

and see if there is anything weird in there like a configuration for monitor upside down.

Cheers

---

### Post by brnetonboy on 2008-09-02
I logged in as a different user and did a "su" to my normal user. But I can't tell if anything is funny in /etc/X11/xorg.conf !

```


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
EndSection

```

---

### Post by p_quarles on 2008-09-02
There won't likely be anything in xorg.conf. I would suggest (if you can open up Gnome-terminal) running
```
xrandr --prop
```
You'll have to read the upside down results, but it might tell you what the bad setting is calling itself.

---

### Post by keplerspeed on 2008-09-02
What about using xfix? I do believe that will recreate your x configuration. Where did you alter your screen resolution and orientation?

---

### Post by brnetonboy on 2008-09-02
> **p_quarles said:**
> There won't likely be anything in xorg.conf. I would suggest (if you can open up Gnome-terminal) running
```
xrandr --prop
```
You'll have to read the upside down results, but it might tell you what the bad setting is calling itself.

my problem was that when logged in as that user nothing displayed except for the background color and the cursor (upside down).

however, I noticed that when i pressed my keyboard shortcut to bring up the shell, the cursor turned into that blinky I cursor, indicating text. so i figured that the shell actually was there, even though I coudldn't see it!!

so I blindly typed this in and it worked!!!!

```

xrandr -o normal

```

---

### Post by balagosa on 2008-09-12
can I steal your thread? I have the same problem...

I tried what you did...but when I typed **xrandr -o normal**, everything went black. The projector also displays nothing.

---

### Post by thirdd on 2008-11-05
Hello everybody,

First of all thanks for this nice forum ... it helped me fix a lot of problems.
But unfortunately I am stuck with this one:

I also changed my screen-orientation to upside down and got an empty desktop.

I already run xfix, reconfigured xserver via 
```
sudo dpkg-reconfigure xserver-xorg  
```
and copied the xorg.xconf from the Live as described [here ]("http://ph.ubuntuforums.com/showthread.php?t=727005")
**but nothing worked out**.

As i have no keyboard shortcut for a terminal I cannot open a terminal and try xrandr.

[B]Is there anybody out there who knows how to get the xserver back to its real old configuration and normal screen orientation?
[/B]
Thanks in advance for your help

---

### Post by [tke]PB506 on 2009-04-28
> **brnetonboy said:**
> my problem was that when logged in as that user nothing displayed except for the background color and the cursor (upside down).

however, I noticed that when i pressed my keyboard shortcut to bring up the shell, the cursor turned into that blinky I cursor, indicating text. so i figured that the shell actually was there, even though I coudldn't see it!!

so I blindly typed this in and it worked!!!!

```

xrandr -o normal

```



That worked like a charm.  Thank god for guest sessions or else I would have had to read this whole thread upside down while trying to figure out how to fix my display.  I guess that teaches me not to do stupid things like orient my screen upside down:lolflag:  Thanks a lot brnetonboy!

---

