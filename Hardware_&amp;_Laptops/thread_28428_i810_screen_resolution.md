---
title: "i810 screen resolution"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by Someone on 2005-04-20
hi,
i just installed ubuntu hoary on a Dell OptiPlex GX60 everything went perfect (except some proxy settings). Except my screen resolution. Its stuck at 640x480@60hz. I tried almost everything.

1. 855resolution dont work
#Chipset: 845G
#Unknow VBIOS structure
I had to change a line in the source to *bios_type=0 but when i change it 855resolution cant compile anymore (v2 and v3)

2. Change x.org config to use only mode 1024x768... dont work
3. Install Intel linux driver ... no effect
4. Used dpkg-reconfigure xserver-xorg ... no succes

could ANYONE _PLZ_ help me
(sorry for my english)

---

### Post by heimo on 2005-04-20
Have you tried custom modeline and setting HorizSync and VertRefresh? Hints on this thread :
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")
 
If it's about modeline, you should see it in xorgs log - hopefully it's just that and not a driver problem. Could you post your xorg.confs Monitor section and errors and warnings from log? (logfiles exact name in that thread abowe)

---

### Post by Someone on 2005-04-20
part of my xorg.conf

```
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536
EndSection

Section "Monitor"
	Identifier	"DELL E772p"
	Option		"DPMS"
	HorizSync	31-101
	VertRefresh	60-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E772p"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection
```

i added a x log dont know if this is the right one

---

### Post by heimo on 2005-04-20
I don't know if this makes any difference, but I'd use these values:
```

Section "Monitor"
	Identifier	"DELL E772p"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

```
 
Source:
[http://support.dell.com/support/edocs/monitors/e772p/en/spec/spec.htm?c=us&l=en&s=gen&cs]("http://support.dell.com/support/edocs/monitors/e772p/en/spec/spec.htm?c=us&l=en&s=gen&cs")=
 
However, I believe this:
```
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 78.8 MHz Image Size: 300 x 225 mm
(II) I810(0): h_active: 1024 h_sync: 1040 h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) I810(0): v_active: 768 v_sync: 769 v_sync_end 772 v_blanking: 800 v_border: 0
``` 
is the key to solution, making a new modeline out of those values. I've seen someone here do it. Unfortunately I'm not at my Linux box and... 
 
Here it is (mendicants post):
[http://www.ubuntuforums.org/showthread.php?t=26284&highlight=Supported+additional+Video+Mode]("http://www.ubuntuforums.org/showthread.php?t=26284&highlight=Supported+additional+Video+Mode")
 
Something like this to Monitor section...
```
 
Modeline "1024x768" 78.8 1024 1040 1136 1312 768 769 772 800

```
 
EDIT: Also be sure to check enchos post!

---

### Post by Someone on 2005-04-20
this is what i made of my monitor section:

```
Section "Monitor"
	Identifier	"DELL E772p"
	Option		"DPMS"
	Modeline	"1024x768" 78.8 1024 1040 1136 1312 768 769 772 800
EndSection
```

but still no succes :(
i added the new x log

[edit]
i think there something wrong in this line:

(II) I810(0): Not using mode "1024x768" (no mode of this name)
(1024x768,DELL E772p) mode clock 100000MHz exceeds DDC maximum 110MHz

but i dont know for sure. if this is wrong how do i change the mode clock?

---

### Post by heimo on 2005-04-20
Hmm.. I'll take a better look later. I was hoping that'd have fixed it. I would keep the HorizSync and VertRefresh lines there, but it probably doesn't harm leaving them out on this case.
 
Dot clock / pixel clock is in this case 78.8 which is well in the limits (max 110Mhz). You can't change it without changing other aspects of modeline.
 
This is long shot, but you could try to do a new modeline with gtf (run: gtf 1024 768 60) and copy paste that to the Monitor section. Is it connected with d-sub or dvi cable? (EDIT: let me answer, d-sub - there is no DVI input)
 
Try
```
 
Section "Monitor"
  Identifier	"DELL E772p"
  Option		"DPMS"
  HorizSync	30-70
  VertRefresh	50-160
  Modeline "1024x768@85" 100.94 1024 1056 1432 1464 768 782 793 807
EndSection
 

```

---

### Post by Someone on 2005-04-20
ok theres a little progress now... the refresh rate changed from 60Hz to 85Hz.
But the resolution still wont change.

Do you plz have other options, im almost at the point that i will pick up my computer and trow him out of the window (from the 5th floor).

thx in advance

[edit]
gtf 1024 768 60:
Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
-> no succes

---

### Post by heimo on 2005-04-20
Substitute i810 with vesa - in other words, use vesa driver. That could give you a better resolution and some time to get a better solution (if even neccessary).

Trust me, I know what you're feeling. I've been through that several times. Probably I wouldn't be helping others on this subject if I didn't know what it's like. Several people just give up and it's a shame for so nice distribution as Ubuntu is.

EDIT: This is good - same chipset, Dell monitor, same problem, unfortunately no solution, but if you can reach [scorpion]("http://www.ubuntuforums.org/member.php?userid=14628") you can ask for xorg.conf and share the secret with rest of us.

Scorpion on this thread:
[http://www.ubuntuforums.org/showthread.php?t=25985](http://www.ubuntuforums.org/showthread.php?t=25985)

---

### Post by Someone on 2005-04-20
really thx for all your time and help ... im now in my windows. im not at work anymore. Tommorow morning ill continue.

Trust me i wont give up, even better: im gonna replace my own windows with ubuntu. :D i know ubuntu will work correct with my nvidia so it wont be a problem.

---

### Post by Someone on 2005-04-21
ok im back at work now.

I tried the vesa driver ... without any luck. My current xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
#	VideoRam	65536
EndSection

Section "Monitor"
  Identifier	"DELL E772p"
  Option		"DPMS"
  HorizSync	30-70
  VertRefresh	50-160
  Modeline "1024x786"  78.8  1024 1040 1136 1312  786 769 772 800  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E772p"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

i also tried different ModeLines, i tried yours, i tried mine with gtf and i tried one from the log file (the current)

i added my log again

[EDIT]
well there is some change again: when i boot up X it starts with a strange screen (in 640x480) with stripes at the top. Then the X Server start in 640x480 as always.

[EDIT2]
I pm'ed scorpion so im waiting for a reply

---

### Post by Someone on 2005-04-21
HEY i found something !

i changed a setting in my BIOS. Video buffer support or something from 1mb to 8mb (max). And now my screen is at 800x600@85Hz! I dont know how this could happen but its better then 640x480. So is there any chance to change my resolution to 1024x768 cause in my bios 8mb is the max. (set option VideoRAM ?)

thx in advance

---

### Post by heimo on 2005-04-21
Strange. Check this matrix of memory requirements on different resolutions and color depths:
 
[http://www.pcguide.com/ref/video/modesBuffer-c.html]("http://www.pcguide.com/ref/video/modesBuffer-c.html")
 
You should be able to run 1600x1200 at 32-bit colors with 8MB memory. But look at what you can do with 1MB: 800x600@16-bits - or... 1024x768@8-bits. I know you don't want 256 color display, but try it anyway.
 
Could you attach your xorg.log? 
 
And put this to Device section:
VideoRam 8192

---

### Post by jamez on 2005-04-21
Check the Dell site for a bios upgrade. I support 200 GX-270s (and some 280s), and we have the same problem with the i865 on-board grafix with RHEL3, which was remedied by the bios update.

Not sure this will help in your case, but worth checking.

---

### Post by Someone on 2005-04-22
Thank you all for your help (and thx to Ubuntu off course)! I finnaly got it to work at 1024x768@85Hz!

I didnt have to update my bios, just put the video frame buffer support to 8mb and its all done.

```

daniel@someone:~$ glxgears
1723 frames in 5.0 seconds = 344.600 FPS
2047 frames in 5.0 seconds = 409.400 FPS
2149 frames in 5.0 seconds = 429.800 FPS
2148 frames in 5.0 seconds = 429.600 FPS
2147 frames in 5.0 seconds = 429.400 FPS
2148 frames in 5.0 seconds = 429.600 FPS
```

xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
  Identifier	"DELL E772p"
  Option	"DPMS"
  HorizSync	30-70
  VertRefresh	50-160
  Modeline 	"1024x786@75Hz"  78.8  1024 1040 1136 1312  786 769 772 800  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E772p"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Xorg.0.log
[attached]

---

### Post by heimo on 2005-04-22
Great! What a relief!
 
And thanks for posting your working xorg.conf, logs and solution - this may come handy to someone else with same problem.

---

### Post by Orbatos on 2006-02-04
Wow! this is such a life saver, I just set up a dual boot system for a relative when I rebuilt their computer so they could experience desktop linux. The have the sam Dell gx60... I had no idea what I was going to do.

---

### Post by AErickson on 2007-04-26
I have the same Optiplex GX60 I was pretty made that no matter what I did nothing would work.

Changing the video bios from 1 to 8 did the trick. I can get the res so small I can't see the screen. This ROCKS!!! 

I got my first Linus desktop working!!! Should of done this a long time ago.


Thank you for the grunt work.

---

### Post by jerrylamos on 2007-04-26
I had resolution problems(!) with Feisty until near release time.  I've got Intel 82854G graphics which uses i810 driver, and a 1280x1024 LCD monitor.  To run, I did
Ctrl Alt F1
login
sudo dpkg-reconfigure -phigh xserver-xorg
made sure it was using i810 driver (VESA is very slow for me, especially scroll mouse)
I think it might have asked for the video window/storage which is 65536 for me
I don't think there were that many more menus for me.  The -phigh might have something to do with that.
sudo killall gdm
sudo startx

and it has been running nice crisp fast 1280x1024 since.

Cheers, Jerry:)

---

### Post by bodycoach2 on 2007-06-24
I received 2 Optiplex GX60's this week as part of our work towards a Free Geek Central Florida chapter, and experienced the same problems. I updated the bios, increase the video from 1 to 8 meg, and all is well.

---

### Post by mazy13 on 2007-07-10
A massive thanks to the contributers to this thread, I've been stuck on 680x480 and I've done all sorts of edits on xorg.conf based on other advice, none of which appearred to work.

I've got an Intel 82845G in my machine btw and I'm using 6.10 Edgy.

I think the steps that fixed my resolution problem were:

[LIST=1]
[*]Set the horizontal and vertical refresh rates correctly in xorg.conf.
[*]Follow jerrylamos' instructions above to set up the resolutions.
[*]Change the video bios to use 8mb instead of 1mb.
[/LIST]

1280 x 1024 is the highest resolution I selected and this appears to have fixed the tiny login screen problem I had as well.

Thanks again :)

---

