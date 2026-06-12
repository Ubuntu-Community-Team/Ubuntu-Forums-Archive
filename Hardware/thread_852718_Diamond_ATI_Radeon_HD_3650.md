---
title: "Diamond ATI Radeon HD 3650"
date: 2008-07-07
forum: Hardware
---

### Post by pagan_loser on 2008-07-07
Bleg ok i just did all i could here.  Love my Diamond Radeon HD3650 1gb  BUT IT WONT WORK WITH UBUNTU!!!  I love using Ubuntu but i really want to get my video drivers working it would be nice for games and so my screen savers wont chop :( I tried both the Ubuntu recommended ways to install the ATI drivers and Envy but every time when i would restart it doesn't show anything after Ubuntu loading screen it goes black i can hear start up screen and get to the terminal but after nothing it sucks. Any one gots any ideas?

---

### Post by alfalfa31 on 2008-07-11
I have the added advantage of a dumb terminal, so it made troubleshooting this issue easier...

On that note, I'd sure like to see a copy of your xorg.conf and the log output from your last attempt (/var/log/Xorg.0.log).  Can you garner that by making a generic vesa xorg.conf in recovery mode?

This one should work...

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
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


```

---

### Post by shwick on 2008-07-11
I had the same problem with some versions of drivers, but the 8.6 drivers seem to work fine with me.

---

### Post by pagan_loser on 2008-07-12
ok im a total newbe here so how do i get the xorg.conf to post it like it shows up in yours.  I can open it in windows but it is just all in a row not going down.  once i put the drivers in i can use tty1 to bring it up it shows up like that.

---

### Post by alfalfa31 on 2008-07-13
if you must use windows, try getting a smarter notepad (i.e. notepad++)  That might help and it's an open source project, so you won't pay for it...

If you can get to it via ssh, you can edit it right there.  There is a nifty little utility that comes with most distros called nano.  You can type sudo nano -w /etc/X11/xorg.conf and go to town.  If you're using Putty from winders, you can even cut and paste.

Make absolutely SURE you copy the original file (even though it's broken) to something like "xorg.conf.old" or whatever you feel comfortable with.

Easier still, the fact that you can get to it in winders means that it doesn't really matter what's there now.  Just move it to .old and make a new file called xorg.conf, putting that stuff in it.

---

### Post by pagan_loser on 2008-07-13
The Vesa xorg isnt a problem its only when i try to use the restricted drivers so i can use the 3d on my vid card.  It works fine now just all 3d applications and games are slow and choppy even the screensavers.  But when i do install drivers no matter which way i do it be it the ati binary drivers fromt he website or the ones that come with Ubuntu or envy it allwasy boots to a blank screen after ubuntu logo then i have to use ctrl alt f1 to get to TTY1 and reboot then use system restore and use the Xfix option.
> Section "InputDevice"
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

that is what my xorg.conf looks like now

---

### Post by markbuntu on 2008-07-13
Really, I have a Sapphire Radeon HD 3650 1GB and have had no problems at all with the ati drivers from 8.4 through 8.6 except for the usual video playback problems with compiz. It works fine with the restricted driver from the repo and the 8.5 and 8.6 driver from ati. 

Envy caused me nothing but problems in the past so I avoided that and the guide I used to install the driver from ati was this one:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Make sure to run update manager after installing it. It seems to need some kernel updates to work properly. btw, if you have tried installing the 8.6 driver, you really need to get it working with the -19 kernel because the changes to the kernel it made are very difficult to revert.

You can also try the tweaks here once you get it working:


[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by alfalfa31 on 2008-07-13
See, this makes sense now..

The easiest way to fix this is to follow this thread's advice.  It should get you back in business.

[http://no-names.biz/2008/05/31/ati-catalyst-85-in-ubuntu-804/](http://no-names.biz/2008/05/31/ati-catalyst-85-in-ubuntu-804/)

I would suggest that you boot to the recovery console.  That way you'll default to root and won't need the "sudo" stuff.

You'll be making a package for your box but out of the downloadable drivers from ATI.

Let me know how it turns out, or if you have any trouble.

------------------------

Come to think of it, I like the tutorial that markbuntu posted better...

---

### Post by pagan_loser on 2008-07-14
THANK YOU!!!:guitar:
you rock i love it now i didnt know ubuntu did these fancy things its doing now!  I used the one markbuntu posted the second method on the wiki and it works like a charm!!!

So thank you Alfalfa and Markbuntu!

---

### Post by alfalfa31 on 2008-07-14
See, Ubuntu can rock...

---

