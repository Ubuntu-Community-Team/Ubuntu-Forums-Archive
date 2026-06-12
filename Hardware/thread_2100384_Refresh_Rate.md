---
title: "Refresh Rate"
date: 2013-01-01
forum: Hardware
---

### Post by bman on 2013-01-01
I am trying to change my refresh rate to 75hz, which at the moment it is at 60hz.

I have a ATI Radeon 5850 card, with the 12.10 drivers on 12.04 Ubuntu, my maximum refresh rate is 75hz that is what I want, but the ATI control panel is not letting me change it.

I opened up Compiz and change it in there, but didn't actually change it, ATI still displayed 60hz.

Help?

---

### Post by bman on 2013-01-01
I am doing this because most things on my system seem choppy.

I don't know if that is the correct word, but its not smooth, not as smooth as it should be.

I also turned off vsync in Compiz which helped, but still not perfect.

---

### Post by bman on 2013-01-05
Anyone?

HP LP2475w on Ubuntu 12.04, latest 12.11 beta drives from AMD.

I know in Windows I got 75hz......

---

### Post by tgalati4 on 2013-01-05
Although xorg.conf files are not included anymore, you might try putting the following into SCREEN section of /etc/X11/xorg.conf and rebooting:

tgalati4@Dell600m-mint14 ~ $ gtf 1024 768 60

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

```
gtf 1024 768 60
```

Change the 1024 768 60 to your actual screen resolution and desired refresh rate--which would be 75 in this case.

If you don't have an /etc/X11/xorg.conf file you can create one:

[http://ubuntuforums.org/showthread.php?t=1553582](http://ubuntuforums.org/showthread.php?t=1553582)

---

### Post by bman on 2013-01-05
How do I accomplish that?

What is the command to edit that file?

---

### Post by tgalati4 on 2013-01-05
Do a little searching in the forums and you will find it.  

[http://ubuntuforums.org/showthread.php?t=1553582](http://ubuntuforums.org/showthread.php?t=1553582)

See if you have an existing xorg.conf:

Open a terminal:
```
cd /etc/X11
ls -la
cat xorg.conf

```

Because you are running 12.04 and xorg.conf has been deprecated (not supposed to be used anymore), there may be a simpler or alternative method.  Usually the proprietary drivers have a control panel that makes these changes, but apparently yours is broken or there is some incompatibility.

xorg.conf may be deprecated, but you can still find a manual page for it:

```
man xorg.conf
```

Spacebar to page through, "q" to quit.

---

### Post by bman on 2013-01-05
Well a simpler answer would be nice.

The AMD control centre does not allow me to change it, but at the same time says max refresh rate is 75..makes no sense.

---

### Post by bman on 2013-01-06
I can't seem to edit that file.

Also, anyone have any other ideas. Maybe why my AMD control panel is being stupid.

---

### Post by Yellow Pasque on 2013-01-06
Changing your refresh rate isn't going to magically make your system faster. Nevertheless: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

EDIT: you need root/sudo permissions to edit system files
```
gksu gedit /etc/X11/xorg.conf
```

Running the AMDCCCLE with root permissions might help too...

---

### Post by bman on 2013-01-10
Going to add this to this thread because I think it might be related, or caused by it.

Part of my issues is this thing that happens when I drag my windows. I hope you can see what I am talking about from the picture. See the yellow/white that happens, all windows do that when I drag them. More or less of it, but always. Anyone seen this before, fixed it? 

[IMG]http://i.imgur.com/Dbf7b.jpg[/IMG]

---

### Post by bman on 2013-01-10
> **Temüjin said:**
> Changing your refresh rate isn't going to magically make your system faster. Nevertheless: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

EDIT: you need root/sudo permissions to edit system files
```
gksu gedit /etc/X11/xorg.conf
```

Running the AMDCCCLE with root permissions might help too...

If I am not suppose to be using that file anymore in 12.04, then I don't really want to edit it. And yes, I only use the AMD settings with root.

---

### Post by tgalati4 on 2013-01-10
The use of xorg.conf is being deprecated, but you can still use it.  It is helpful for working around problems such as what you are experiencing.

Did you run the gtf command that I posted earlier?  Did you cut and paste the output of that command into xorg.conf?

The streaks that you are seeing during wobbly windows is lack of anti-aliasing.  It is either turned off or it is not working correctly with your graphics card.

---

### Post by bman on 2013-01-11
I don't see any gtf command.

Only

```
cd /etc/X11
ls -la
cat xorg.conf
```

A step by step would be nice.

---

### Post by tgalati4 on 2013-01-11
```
gtf 1280 1024 75
```

---

### Post by bman on 2013-01-11
Alright,

So I am suppose to type that with my desired resolution and refresh rate?

Then it's suppose to output info? I put that info into xorg.conf? Save it....where exactly do I enter that into that file?

Reboot?

---

### Post by Yellow Pasque on 2013-01-11
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)

---

### Post by bman on 2013-01-11
If I could figure this out by looking at that link then I wouldn't have needed to post here.

This is my xorg.conf file.

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

and this is the output of the gtf command.

```
  # 1920x1200 @ 75.00 Hz (GTF) hsync: 93.97 kHz; pclk: 246.59 MHz
  Modeline "1920x1200_75.00"  246.59  1920 2064 2272 2624  1200 1201 1204 1253  -HSync +Vsync
```

I don't see where it goes.

---

### Post by Yellow Pasque on 2013-01-11
You copy the Modeline and paste it in the Monitor section (just as the example shows ;) ).

---

### Post by bman on 2013-01-11
Alright, I did that. Assuming I did it correctly.

Nothing happened, I rebooted, nothing.

---

### Post by tgalati4 on 2013-01-12
Now you know why they deprecated xorg.conf, because it was confusing to set up for most people.

Page through your error file and post any errors that might be helpful:

```
less /var/log/Xorg.0.log
```

Also paste your xorg.conf file.

I don't think you can get 75 Hz at 1920x1080.  Most LDC flat panels only operate at 60 Hz.  75 and 85 Hz is for CRT (old style, 4:3) displays that would visibly flicker at 60 Hz under flourescent lights.

---

### Post by bman on 2013-01-12
I didn't find any errors.

Also, it's 1920x1200, not 1080. Though you might be right. I just remember Windows being able too, plus I didn't have screen issues. I guess the drivers just aren't working that great with my system.

---

### Post by tgalati4 on 2013-01-13
Paste in the modeline for 1920 1200 60 into xorg.conf and reboot.  See if that works any better.  Do some research on your monitor to see what the maximum refresh rate is.  For most LCD's it's 60 Hz, because the LCD crystals have a slow refresh, they don't flicker like the old CRT monitors.  If you are getting artifacts on the screen, then it's possible that there are problems with the graphics driver at maximum resolution.  This is fairly common with linux graphics drivers, unfortunately.

---

