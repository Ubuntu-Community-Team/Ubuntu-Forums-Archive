---
title: "Inspiron E1505 Resolution"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by UltraMathMan on 2006-07-18
I have a 15.4" widescreen Inspiron E1505 (Unbuntu 6.06) and cannot get any widescreen resolutions through System->Preferences->Screen Resolution. I have a 256MB ATI MOBILITY RADEON X1400 with HyperMemory and the 915resolution package outputs:

"ATI chipset detected.  915resolution only works with Intel 800/900 series graphic chipsets."

from my xorg.conf file(complete xorg.conf file attatched):


Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Any help would be greatly appreciated. Thank you.

---

### Post by nicbink on 2006-07-19
You won't need the 915 hack.  I have the E1705 with the same ATI card and I got 1920x1200 running w/o it.

First is to make sure that you're running the FGLRX driver

```
fglrxinfo
```

if the return says anything about MESA then you need to get the ATI driver working.

if the above returns ATI Technology blah blah blah then do the initial config

```
aticonfig --initial
```

then restart the X server (CTRL + ALT + BACKSPACE) (make sure all apps closed first)

see if that helps, if not then try editing the xorg.conf to include only the resolutions you want to use (1280x800 i presume)

--------------

side note: Were you a bit angry with Dell/ATI when you found out that the ATI 256 card you bought was really a 128 with 128 shared system memory?  I called Dell to complain that they sent me the wrong card but he kept calling it 256mb HyperMemory, it's not 128 it's 256 HYPERMEMORY.  So I looked up HyperMemory on ATI's site and lo-and-behold it's 128 + 128 shared.  How does the branding HyperMemory signify shared????

---

### Post by UltraMathMan on 2006-07-19
Thanks, I used [http://www.ubuntuforums.org/showthread.php?t=83973&highlight=adding+resolutions]("http://www.ubuntuforums.org/showthread.php?t=83973&highlight=adding+resolutions") to reconfigure xserver and managed to get 1680x1050 (although I also selected 1440x900 Screen Resolution doesn't offer it as an option) I'll keep playing with it and see what happens. 

Oh, and I did some research on the video card before I purchased the system so I knew it was a 128mb card. I was more upset with the partioning of my HD to give Norton Ghost a backup partion (20 of 100 GB) and the crap they installed with XP Pro as well as missing and incorrect CDs. ](*,)

---

### Post by Devile on 2006-09-08
> **nicbink said:**
> You won't need the 915 hack.  I have the E1705 with the same ATI card and I got 1920x1200 running w/o it.

First is to make sure that you're running the FGLRX driver

```
fglrxinfo
```

if the return says anything about MESA then you need to get the ATI driver working.

if the above returns ATI Technology blah blah blah then do the initial config

```
aticonfig --initial
```

then restart the X server (CTRL + ALT + BACKSPACE) (make sure all apps closed first)

see if that helps, if not then try editing the xorg.conf to include only the resolutions you want to use (1280x800 i presume)

--------------

side note: Were you a bit angry with Dell/ATI when you found out that the ATI 256 card you bought was really a 128 with 128 shared system memory?  I called Dell to complain that they sent me the wrong card but he kept calling it 256mb HyperMemory, it's not 128 it's 256 HYPERMEMORY.  So I looked up HyperMemory on ATI's site and lo-and-behold it's 128 + 128 shared.  How does the branding HyperMemory signify shared????



I tried all those codes and no matter that i type in i get a command not found
 line...  so what's going on?

---

### Post by ysr on 2006-09-13
> **Devile said:**
> I tried all those codes and no matter that i type in i get a command not found
 line...  so what's going on?

Sorry, I am not sure from the post if you have installed the fglrx dirvers or not. If not you will need to install it using```
sudo apt-get install xorg-driver-fglrx-dev
``` as these do not ship with the default distribution. You will have to enable the universe in you sources.list.

For me, once I downloaded the driver all I had to do was

```

sudo aticonfig --initial
sudo aticonfig --resolution=0,1280x800

```

The leading 0 in the resolution is for the screen number (i.e. first screen)

On a (probably) related note, when I try to use
```

aticonfig --set-powerstate=N

```
it works fine sometime, and other times I suddenly get a blank white/black screen and the system has to be hard rebooted. Does anyone experience the same problem? Any idea what might be causing it?

---

### Post by ampop on 2006-09-15
I had this message:
```
ampop@acer-laptop:~/Desktop$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

ampop@acer-laptop:~/Desktop$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
```
There is any way to fix this?
Thank you.

---

### Post by ampop on 2006-09-15
> **ampop said:**
> I had this message:
```
ampop@acer-laptop:~/Desktop$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

ampop@acer-laptop:~/Desktop$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
```
There is any way to fix this?
Thank you.
It's solved!!!
I missed 'sudo'.:-\" 
After:```
sudo aticonfig --initial
```
The problem was solved.

Thank you very much.=D>

---

### Post by mattyj on 2006-09-23
Do you get good graphics card accelleration under ubuntu with this card?   I have always used nVidia cards in linux prior as they are well supported, but the E1505 is a good deal and they just took away the option of an nvidia card.

Thank You,

MJ

---

### Post by ampop on 2006-09-23
My graphical exigence it's low. For now I haven't any problem.

---

### Post by Daniel15 on 2006-09-23
The ATI drivers that come with Ubuntu (version 8.25.18 I think) do not work as well as the latest ATI drivers (8.29.6). See [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) (method 2) for a detailed tutorial on installing the ATI drivers :)

> Do you get good graphics card accelleration under ubuntu with this card?
Yeah, it seems to work quite well

---

### Post by neuropsychguy on 2006-09-26
> **ampop said:**
> It's solved!!!
I missed 'sudo'.:-\" 
After:```
sudo aticonfig --initial
```
The problem was solved.

Thank you very much.=D>

I just wanted to add that the best way to get the proper resolutions showing up if sudo aticonfig --initial doesn't work properly is to run the command ```
sudo aticonfig --force --initial
```

Works like a charm for me. Of course, this is assuming that the only thing that doesn't work is having the proper resolutions show up.

---

