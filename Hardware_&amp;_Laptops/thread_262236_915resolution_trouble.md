---
title: "915resolution trouble"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by Monkus on 2006-09-21
Ok, here we go with the age old widescreen resolution question. I am on a Gateway MX6121. It is capable of 1280x800 res. I did the old apt-get install 915resolution and now I have 1280x800, but it is too big. The desktop scrolls from side to side and up and down when I move the mouse to the sides or the top and bottom. I am a Linux/Ubuntu newb, and any help or insight would be greatly appreciated. Thank you in advance.

---

### Post by xyz on 2006-09-21
Some folks are talking about it here. Sorry I can't help you more with this issue.
[http://ubuntuforums.org/showthread.php?p=1432845](http://ubuntuforums.org/showthread.php?p=1432845)

---

### Post by Monkus on 2006-09-21
Hey thanks, I'll check it out.

---

### Post by Monkus on 2006-09-21
Well, I checked out that link. What I could understand didn't help. But I appreciate the quick reply. I'll keep working on it and if anybody has any suggestions, let me know. THanks.

---

### Post by xyz on 2006-09-22
Did you take a look at this:
[i915Driver]("https://help.ubuntu.com/community/i915Driver")

and [Here]("http://www.dhost.info/zachstruck/") This Here 2nd link talks about installing on a different laptop than yours but it treats the subject of resolution.

---

### Post by Monkus on 2006-09-22
Thanks for the links. I have reinstalled Ubuntu and followed the instructions for installing 915resolution. Yet, I still have the scrolling desktop. Here is the contents of my xorg.conf



Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

I may try and reinstall again and see if I can get it to work. Thanks for everyones help. Oh yeah, and if you don't know I'm on a Gateway MX6121, 15.4 LCD. Thanks.

---

### Post by Monkus on 2006-09-22
I have an update. When I use 915resolution, it changes the display to 1280x800, and that is too large and I have to scroll to see the entire desktop. When I remove it completely, it displays at 1024x768. I have followed all the instructions, apt-get, synaptic install. I have reinstalled Dapper, tried Edgy. Nothing seems to get it. Please help save my hair (I'm pulling it) Any help would be appreciated. Thanks.

---

### Post by Monkus on 2006-09-22
Well. No matter what I try. 1280x800 on the Gateway MX6121 doesn't seem to want to happen. Perhaps down the road after some updates and such it will, but for now it seems like a no go  :sad: If someone figures this out, please let me know.

---

### Post by coffeecat on 2006-09-23
I tried googling 'gateway mx6121'. I could find only one link that gave detailed specifications and that said the screen resolution was only 1024x768, which is the resolution that does work on your machine. It may be that the information on that link was wrong, but if your machine is only capable of 1024x768, that would explain the scrolling problem you get.

Are you sure of the resolution? Where did you get the information from?

---

### Post by reh4c on 2006-09-23
> **coffeecat said:**
> I tried googling 'gateway mx6121'. I could find only one link that gave detailed specifications and that said the screen resolution was only 1024x768, which is the resolution that does work on your machine. It may be that the information on that link was wrong, but if your machine is only capable of 1024x768, that would explain the scrolling problem you get.

Are you sure of the resolution? Where did you get the information from?

I found this information:  
[http://rob.pectol.com/content/view/13/27/]("http://rob.pectol.com/content/view/13/27/")
See about half-way down the page.  :idea:

---

### Post by Monkus on 2006-09-23
hey thanks for the help. I was using 1280x800 on XP on this machine and that is where I got the information from. Perhaps I was wrong and XP does something special to get that resolution.I will try the link you posted and let you know what happens. Thanks again.

---

### Post by Monkus on 2006-09-23
AHHHHHHHH!!!!! Ok, so i tried the script and it does the same thing. Scrolling desktop. I will have to do a little more study on this problem. Except, now I cannot undo that little script install, crud. OH well, back to the books (and forums, and google...).

---

### Post by Monkus on 2006-09-23
Well, I think I have found out what the problem is. I think XP was doing soemthing special because I foundd 2 reviews of this machine that specify 1024x768. 915resolution found 1280x800 and that is what showed up in my xorg.conf, but it doesn't seem to work. So, I will have to stick with 1024x768 even though it seems stretched and somewhat fuzzy, unless something else comes up. It's not so bad, I just got used to the other. Thanks everyone for all your help. I will return the favor whenever I can.

---

### Post by reh4c on 2006-09-23
I'm sorry you couldn't get it working.

---

### Post by Monkus on 2006-09-24
Ok here are the specs on the monitor

    * 15.4-inch active matrix (TFT) LCD color display
    * Maximum panel resolution: 1280 × 800.
    * Maximum color depth: 32-bit (16.7 million colors) at 1024 × 768 and 262,144 colors at 1280 × 800
    * LCD supported video modes
          o XGA
          o SXGA+
          o WXGA 
    * LCD maximum refresh rate: 60 Hz 

If anyone can help that would be great.

---

### Post by coffeecat on 2006-09-24
> **Monkus said:**
> Ok here are the specs on the monitor

    * 15.4-inch active matrix (TFT) LCD color display
    * Maximum panel resolution: 1280 × 800.
    * Maximum color depth: 32-bit (16.7 million colors) at 1024 × 768 and 262,144 colors at 1280 × 800

That's most interesting and rather bizarre; I've never come across that. I thought it was odd that a 15.4" lcd screen was only giving a resolution of 1024x768.

Clearly your screen is capable of 1280x800, but only at a colour depth of thousands of colours rather than millions - for whatever reason, a video ram limitation perhaps. So perhaps Windows is displaying 1280x800 only at the lesser colour resolution. Might be worth checking that. If so then perhaps if you set your Ubuntu colour depth at thousands you might get 1280x800. Trouble is - Ubuntu doesn't have a handy GUI utility to do that. (Unlike Fedora which has had one since before core 3 - hint to devs - oh, but they're not active on this forum, are they? :().

You might be able to reconfigure colour depth with:

```
sudo dpkg-reconfigure xserver-xorg
```but I can't be sure as I've never had occasion to use that command. Perhaps someone else can comment.

---

### Post by Monkus on 2006-09-24
So perhaps if I set it to 16 instead of 24 it will work? I will give that a try and see what happens, although it may be a mistake due to my lack of knowledge. I'll let you know what happens.

---

### Post by Monkus on 2006-09-24
Well, I tried that and it didn't work. Dagnabit. this is the only thing that didn't work right out of the box. I sure hope that this gets some attention in Edgy. That would be great.

---

### Post by Monkus on 2006-09-24
Ok, I rebooted into the windows partition and XP says 1280x800 at 32bit. YAAARRRGGGG. This is almost silly.

---

### Post by Monkus on 2006-09-24
Ok, here is some more information. this is from the Xorg.0.log

(II) I810(0): Generic Monitor: Using hsync range of 48.00-50.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 59.00-61.00 Hz
(II) I810(0): Not using mode "1280x800" (no mode of this name)
(II) I810(0): Not using mode "1200x800" (no mode of this name)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(--) I810(0): Display dimensions: (330, 210) mm
(--) I810(0): DPI set to (78, 92)

and from my xorg.conf

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1200x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1200x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1200x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1200x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1200x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1200x800" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


With any luck someone will see this and see something that I cannot. Thanks for your help. and a serious thanks to coffeecat.

---

### Post by coffeecat on 2006-09-25
Sorry, I'm out of ideas - it's quite baffling. But there's one thing I've noticed:
From your monitor specs:

> LCD maximum refresh rate: 60 Hzand from your xorg.conf:

>  Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-60
    VertRefresh    50-75
EndSectionMight be safer changing that vertrefresh rate. (Check what refresh rate you're getting in System >Preferences > Screen Resolution first.)

What's even stranger is that on my Sony Vaio laptop with Intel 915GM graphics I'm getting 1280x800 @ 60Hz absolutely fine (and with three distros) and my Ubuntu xorg.conf Monitor section only has:

>  Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSectionNo VertRefresh and no HorizSync. :? I could post the Screen and Device sections if you want. Let me know.

**Edit:** I've just had a look in the SuSE and Fedora xorg.conf files on my Sony and they both have HorizSync and VertRefresh lines, but different ones - Fedora VertRefresh = '60-60' and Suse VertRefresh = '50-60'. And there are a whole load of other variations in the other sections too. I could post the relevant parts of all three if you like and then you could have many happy hours copying and pasting different bits into your xorg.conf and see what happens. :wink: At your own risk, of course!

---

### Post by Monkus on 2006-09-25
Thanks for your response. I don't know where to go from here really. I think it may be the driver. I set the refresh rates and changed the driver to vesa. then the login screen came up great, 1280x800, but would not boot X. I was so close. Anyway, I may try and see what alternative drivers I could use  or something.

---

### Post by coffeecat on 2006-09-25
Well - hmm. I'd be surprised if it's the driver. I've got the same Intel graphics chipset as you on my laptop and it's using the same i810 driver. No problems. In fact it renders PlanetPenguin Racer a treat.

---

### Post by Monkus on 2006-09-25
Yeah, I tried vesa again, but that didn't work. I reconfigued xserver and reinstalled 915resolution, but I just get the same result. I guess I'll have to wait and see if Edgy can fix it. We'll see. Other than that, I'm really close to deleting my Windows partition. I would love to go linux completely on my laptop, I still have to use Mac on the desktop because I run a video production company and have to use Final cut pro. I'm still waiting for linux video editing, I don't think I will have to wait long though the way development is going. Ok, I digress. Thanks for all your help coffeecat. I'll keep trying and if I get anywhere I'll let you know.

---

### Post by ridgerunner7 on 2006-09-25
Sounds to me like xorg isn't finding the mode it needs in VBIOS. What is the output of "915resolution -l"? Here's what mine looks like:

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $29f
Mode Table Entries: 39

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 7c : 1280x800, 8 bits/pixel
Mode 7d : 1280x800, 16 bits/pixel
Mode 7e : 1280x800, 32 bits/pixel

Note my last 3 modes are 1280x800 which will be missing, I suspect, in your output, although I've been wrong before. :rolleyes:

---

### Post by Monkus on 2006-09-25
Well, when I installed 915resolution 1280x800 was on the list. I set it to use that mode and I even tried to set it to that mode in 16bit but the desktop ends up too large and I have to scroll to see the whole desktop. I don't know how to get it to fit the screen. I'll come back when I'm on the linux machine and post the 915resolution -l results. Be back in a sec.

---

### Post by Monkus on 2006-09-25
Ok, here is the results of the 915resolution -l

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel

---

### Post by ridgerunner7 on 2006-09-25
[edit]: your output should work.

perhaps specifying resolution in /etc/default/915resolution will help? Set
xreso=1280
yreso=800

or perhaps you need to set "ForceBIOS" in the "Device" section of xorg.conf? Which they recommend [here]("https://help.ubuntu.com/community/i915Driver")

or perhaps you need to set a modeline in the "Monitor" section of xorg.conf? I used to have to do that in Breezy days (or perhaps that was in Debian Sarge days, can't remember). To calculate a modeline I used to use gtf. Something like this: gtf 1280 800 60

Hopefully these aren't all rabbit trails!

---

### Post by Monkus on 2006-09-25
Ok, I have tried those things, but perhaps I should try again. The only thing I don't understand is this option for 915resolution on editing the xorg.conf

add this line
Option "ForceBIOS" "1920x1440=1400x1050"

Now, if I want 1280x800 what do I put. I don't understand the significance of the 1920x1440. If you use 1920x1440=1400x1050, what would you use for XXXXxXXXX=1280x800? Hmmmmmmmmmm

---

### Post by ridgerunner7 on 2006-09-25
I think (read: "don't *know*") you want to force what you are getting 1024x768 to 1280x800 so:
Option "ForceBIOS" "1024x768=1280x800"

---

### Post by Monkus on 2006-09-25
ok, tried it all with multiple configurations. No go. I am baffled. ForceBios, 915, Modeline,16-bit 24-bit, all of it does the same thing. Desktop too big for screen, must scroll to see it all. I'm stuck on 1024x768 with fuzzy stretched text and screen. Oye! Well, I have to rest my brain on this one. I'll get back to it later if someone comes up with something new. Thanks for your help ridgerunner7. Let me know if you think of anything.

---

### Post by Monkus on 2006-09-27
Ok, I think I found something that may shed some light on this. I think it has to do with the refresh rates. In the Xorg.0.log it says something about hsync and vsync not within range. I would paste it here but I am on the mac while I reconfigure xserver. I'll let you know what happens.

---

### Post by Monkus on 2006-09-27
Ok, In Xorg.0.log I get "mode clock 83.46MHz exceeds DDC maximum 80MHz" I don't know what that means, but It definately means something.

---

### Post by coffeecat on 2006-09-27
> **Monkus said:**
> Ok, I think I found something that may shed some light on this. I think it has to do with the refresh rates. In the Xorg.0.log it says something about hsync and vsync not within range.

Ahem - cough, cough - ahem. Check out my post #21. :wink: I did point out the discrepancy between your system specs of refresh rate of 60 and the xorg.conf VertRefresh values of 50-75.

Have you tried changing VertRefresh to 60-60? This should force a refresh rate of 60. Might be worth a try. Can't help you with the HorizSync value though.

---

### Post by Monkus on 2006-09-27
Coffeecat, I did try that and I got the same result. I think it must have something to do with this mode clock thing.

---

### Post by barak on 2006-09-28
I have been having the same sort of trouble Monkus.

In windows I can get 1152x864 on my laptop LCD and my external CRT at the same time.  In linux it is 1024x768 on both.  I can get the CRT to go higher but only at 60Hz.

I am trying to use the 015resolution to implement 1152x864 @ 70Hz for the CRT only - which I know it can do - and all I get back is 1024x768.

The worst things is - from the log files - I can set the resolution for the LCD only - which it then won't implement as it says the panel is 1024x768 - but for the CRT the log says there is no built-in mode called 1152x864!!

here are the relevant files: xorg.conf
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML (Internal)"
	Driver		"i810"
#	Option		"VBERestore" 		"no"
	Option		"DisplayInfo"		"false"
	Option		"MonitorLayout" 	"CRT,LFP"
	Option		"DevicePresence"	"yes"
#	Option		"ForceBIOS"		"1600x1200=1152x864"
	BusID		"PCI:0:2:0"
	Screen		1
EndSection

Section "Device"
	Identifier	"915GM/GMS/910GML (External)"
	Driver		"i810"
#	Option		"VBERestore" 		"no"
	Option		"DisplayInfo"		"false"
	Option		"MonitorLayout" 	"CRT,LFP"
	Option		"DevicePresence"	"yes"
	Option          "ForceBIOS"             "1024x768=1152x864"
	BusID		"PCI:0:2:0"
	Screen		0
EndSection


Section "Monitor"
	Identifier	"Internal LCD"
#	HorizSync	28-49
	VertRefresh	60-60
	Option		"DPMS"
EndSection

Section "Monitor"
	identifier 	"External Monitor"
	HorizSync	30-70
	VertRefresh	50-100
	Modeline 	"1152x864"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML (Internal)"
	Monitor		"Internal LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"VGA"
	Device		"915GM/GMS/910GML (External)"
	Monitor		"External Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Xinerama"
	Screen		0 "VGA" 0 0
	Screen		1 "LCD" RightOf "VGA"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
#	Option		"Xinerama" "on"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

and the xorg log:
```

(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Xinerama"
(**) |-->Screen "VGA" (0)
(**) |   |-->Monitor "External Monitor"
(**) |   |-->Device "915GM/GMS/910GML (External)"
(**) |-->Screen "LCD" (1)
(**) |   |-->Monitor "Internal LCD"
(**) |   |-->Device "Intel Corporation Mobile 915GM/GMS/910GML (Internal)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"

(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(**) I810(0): Option "DisplayInfo" "false"
(**) I810(0): Option "DevicePresence" "yes"
(**) I810(0): Option "MonitorLayout" "CRT,LFP"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) I810(0): Chipset: "915GM"
(--) I810(0): Linear framebuffer at 0xC0000000
(--) I810(0): IO registers at addr 0xB0080000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 110080 total, 1 used
(II) I810(0): Checking Available AGP Memory: 440316 kB available (total 440320 kB, used 4 kB)
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(==) I810(0): VideoRAM: 131072 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 3412
(II) I810(0): Using new Pipe switch code
(**) I810(0): Device Presence: enabled.
(II) I810(0): Display Presence: CRT: attached: TRUE, encoder: TRUE
(II) I810(0): Display Presence: TV: attached: FALSE, encoder: TRUE
(II) I810(0): Display Presence: DFP (digital flat panel): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: LFP (local flat panel): attached: TRUE, encoder: TRUE
(II) I810(0): Display Presence: CRT2 (second CRT): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: TV2 (second TV): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: DFP2 (second digital flat panel): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: LFP2 (second local flat panel): attached: FALSE, encoder: FALSE
(**) I810(0): Display Info: disabled.
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0): 	LFP (local flat panel)
(II) I810(0): No display size information available for pipe B.
(**) I810(0): Primary head is using Pipe A
(--) I810(0): Maximum frambuffer space: 130904 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: SAM  Model: 1057  Serial#: 1146106167
(II) I810(0): Year: 2001  Week: 34
(II) I810(0): EDID Version: 1.1
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate
(II) I810(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) I810(0): Gamma: 2.26
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): redX: 0.645 redY: 0.321   greenX: 0.285 greenY: 0.600
(II) I810(0): blueX: 0.142 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 720x400@88Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@67Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@56Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 832x624@75Hz
(II) I810(0): 1024x768@87Hz (interlaced)
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) I810(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) I810(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) I810(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 56.2 MHz   Image Size:  306 x 230 mm
(II) I810(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) I810(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 94.5 MHz   Image Size:  306 x 230 mm
(II) I810(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) I810(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) I810(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) I810(0): Serial No: H8OR803917
(II) I810(0): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(0): Maximum space available for video modes: 12288 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-70
(II) I810(0): 	VertRefresh 50-160
Mode: 30 (640x480)
Mode: 32 (800x600)
Mode: 34 (1024x768)
Mode: 38 (1280x1024)
Mode: 3a (0x0)
Mode: 3c (1920x1440)
Mode: 41 (640x480)
Mode: 43 (800x600)
Mode: 45 (1024x768)
Mode: 49 (1280x1024)
Mode: 4b (0x0)
Mode: 4d (1920x1440)
*Mode: 50 (640x480)
*Mode: 52 (800x600)
*Mode: 54 (1024x768)
*(WW) (1280x1024,External Monitor) mode clock 135MHz exceeds DDC maximum 110MHz
Mode: 58 (1280x1024)
Mode: 5a (0x0)
*(WW) (1920x1440,External Monitor) mode clock 234MHz exceeds DDC maximum 110MHz...
Mode: 5c (1920x1440)
Mode: 60 (0x0)
Mode: 61 (0x0)
...
(II) I810(0): External Monitor: Using hsync range of 30.00-70.00 kHz
(II) I810(0): External Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(II) I810(0): Attempting to use 85.00Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 85.14Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 85.01Hz refresh for mode "640x480" (850)
(--) I810(0): Display dimensions: (320, 240) mm
(--) I810(0): DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules/libvgahw.so
(**) I810(1): Depth 24, (--) framebuffer bpp 32
(==) I810(1): RGB weight 888
(==) I810(1): Default visual is TrueColor
(**) I810(1): Option "DisplayInfo" "false"
(**) I810(1): Option "DevicePresence" "yes"
(**) I810(1): Option "MonitorLayout" "CRT,LFP"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(1): Integrated Graphics Chipset: Intel(R) 915GM
(--) I810(1): Chipset: "915GM"
(--) I810(1): Linear framebuffer at 0xC0000000
(--) I810(1): IO registers at addr 0xB0080000
(II) I810(1): 2 display pipes available.
(II) I810(1): detected 7932 kB stolen memory.
(II) I810(1): Monitoring connected displays enabled
(II) I810(1): Will attempt to tell the BIOS that there is 12224 kB VideoRAM
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12224 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(1): BIOS now sees 12224 kB VideoRAM
(--) I810(1): Pre-allocated VideoRAM: 7932 kByte
(==) I810(1): VideoRAM: 12288 kByte
(==) I810(1): video overlay key set to 0x101fe
(**) I810(1): page flipping disabled
(==) I810(1): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(1): BIOS Build: 3412
(II) I810(1): Using new Pipe switch code
(**) I810(1): Device Presence: enabled.
(II) I810(1): Display Presence: CRT: attached: TRUE, encoder: TRUE
(II) I810(1): Display Presence: TV: attached: FALSE, encoder: TRUE
(II) I810(1): Display Presence: DFP (digital flat panel): attached: FALSE, encoder: FALSE
(II) I810(1): Display Presence: LFP (local flat panel): attached: TRUE, encoder: TRUE
(II) I810(1): Display Presence: CRT2 (second CRT): attached: FALSE, encoder: FALSE
(II) I810(1): Display Presence: TV2 (second TV): attached: FALSE, encoder: FALSE
(II) I810(1): Display Presence: DFP2 (second digital flat panel): attached: FALSE, encoder: FALSE
(II) I810(1): Display Presence: LFP2 (second local flat panel): attached: FALSE, encoder: FALSE
(**) I810(1): Display Info: disabled.
(II) I810(1): Currently active displays on Pipe A:
(II) I810(1): 	CRT
(II) I810(1): Currently active displays on Pipe B:
(II) I810(1): 	LFP (local flat panel)
(II) I810(1): No display size information available for pipe B.
(**) I810(1): Secondary head is using Pipe B
(--) I810(1): Using HW Cursor because it's enabled on primary head.
(--) I810(1): Maximum frambuffer space: 12120 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1024x768
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: SAM  Model: 1057  Serial#: 1146106167
(II) I810(0): Year: 2001  Week: 34
(II) I810(0): EDID Version: 1.1
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate
(II) I810(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) I810(0): Gamma: 2.26
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): redX: 0.645 redY: 0.321   greenX: 0.285 greenY: 0.600
(II) I810(0): blueX: 0.142 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 720x400@88Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@67Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@56Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 832x624@75Hz
(II) I810(0): 1024x768@87Hz (interlaced)
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) I810(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) I810(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) I810(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 56.2 MHz   Image Size:  306 x 230 mm
(II) I810(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) I810(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 94.5 MHz   Image Size:  306 x 230 mm
(II) I810(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) I810(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) I810(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) I810(0): Serial No: H8OR803917
(--) I810(1): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(--) I810(1): Maximum space available for video modes: 12120 kByte
(II) I810(1): Using detected DDC timings
(II) I810(1): 	HorizSync 30-70
(II) I810(1): 	VertRefresh 50-160
(WW) I810(1): config file hsync range 28-33kHz not within DDC hsync range 30-70kHz
Mode: 30 (640x480)
Mode: 32 (800x600)
Mode: 34 (1024x768)
Mode: 38 (1280x1024)
Mode: 3a (1152x864)
Mode: 3c (1920x1440)
Mode: 41 (640x480)
Mode: 43 (800x600)
Mode: 45 (1024x768)
Mode: 49 (1280x1024)
Mode: 4b (1152x864)
Mode: 4d (1920x1440)
*Mode: 50 (640x480)
*Mode: 52 (800x600)
*Mode: 54 (1024x768)
*(WW) (1280x1024,Internal LCD) mode clock 135MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,Internal LCD) mode clock 157.5MHz exceeds DDC maximum 110MHz
Mode: 58 (1280x1024)
*(WW) (1152x864,Internal LCD) mode clock 121.5MHz exceeds DDC maximum 110MHz
Mode: 5a (1152x864)
*(WW) (1920x1440,Internal LCD) mode clock 234MHz exceeds DDC maximum 110MHz
Mode: 5c (1920x1440)
...
(II) I810(1): Internal LCD: Using default hsync range of 30.00-70.00 kHz
(II) I810(1): Internal LCD: Using vrefresh range of 50.00-160.00 Hz
(II) I810(1): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) I810(1): Not using built-in mode "1152x864" (width too large for virtual size)
(--) I810(1): Virtual size is 1024x768 (pitch 1024)
(**) I810(1): *Built-in mode "1024x768"
(**) I810(1):  Built-in mode "800x600"
(**) I810(1):  Built-in mode "640x480"
(--) I810(1): Display dimensions: (320, 240) mm
(--) I810(1): DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules/libxaa.so
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/lib/xorg/modules/libramdac.so
(==) I810(1): VBE Restore workaround: enabled.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after preInit:

(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Secondary framebuffer allocation size: 5120 kByte
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 5120 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xffff000 (0x0c164000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xfffb000 (0x12af4000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xfffa000 (0x0a27d000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xffea000
(II) I810(0): Allocated 64 kB for the second scratch buffer at 0xffda000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xe06a1000
(II) I810(0): [drm] mapped SAREA 0xe06a1000 to 0xb7eda000
(II) I810(0): [drm] framebuffer handle = 0xc0520000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): Allocated 3072 kB for the back buffer at 0xf800000.
(II) I810(0): Allocated 3072 kB for the depth buffer at 0xf400000.
(II) I810(0): Allocated 32 kB for the logical context at 0xf3f8000.
(II) I810(0): Allocated 114176 kB for textures at 0xa20000
(II) I810(0): Updated framebuffer allocation size from 5120 to 5320 kByte
(II) I810(0): Updated pixmap cache from 512 scanlines to 562 scanlines
(II) I810(0): 0x81ffcec: Memory at offset 0x00020000, size 5120 kBytes
(II) I810(0): 0x81ffccc: Memory at offset 0x00520000, size 5320 kBytes
(II) I810(0): 0x8204cc0: Memory at offset 0x0ffff000, size 4 kBytes
(II) I810(0): 0x8204ae0: Memory at offset 0x0fffb000, size 16 kBytes
(II) I810(0): 0x8204c54: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81ffd0c: Memory at offset 0x0ffea000, size 64 kBytes
(II) I810(0): 0x81ffd2c: Memory at offset 0x0ffda000, size 64 kBytes
(II) I810(0): 0x8204b08: Memory at offset 0x0fffa000, size 4 kBytes
(II) I810(0): 0x81ffd5c: Memory at offset 0x0f800000, size 3072 kBytes
(II) I810(0): 0x81ffd7c: Memory at offset 0x0f400000, size 3072 kBytes
(II) I810(0): 0x81ffdbc: Memory at offset 0x0f3f8000, size 32 kBytes
(II) I810(0): 0x81ffd9c: Memory at offset 0x00a20000, size 114176 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0xb0080000
(II) I810(0): [drm] Back Buffer = 0xcf800000
(II) I810(0): [drm] Depth Buffer = 0xcf400000
(II) I810(0): [drm] ring buffer = 0xc0000000
(II) I810(0): [drm] textures = 0xc0a20000
(II) I810(0): [drm] dma control initialized, using IRQ 177
(II) I810(0): [drm] Initialized kernel agp heap manager, 116916224
(II) I810(0): [dri] visual configs initialized
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 8 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffda000 (pgoffset 65498)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0f800000 (pgoffset 63488)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f400000 (pgoffset 62464)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x0f3f8000 (pgoffset 62456)
(II) I810(0): Setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane A.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(WW) I810(0): Correcting plane B stride (640 -> 1024)
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1088 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(WW) I810(0): Option "ForceBIOS" is not used
(==) RandR enabled
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(1): Extended BIOS function 0x5f05 failed.
(II) I810(1): Display plane A is enabled and connected to Pipe A.
(II) I810(1): Display plane B is enabled and connected to Pipe B.
(II) I810(1): Enabling plane A.
(II) I810(1): Enabling plane B.
(II) I810(1): Display plane A is now enabled and connected to Pipe A.
(II) I810(1): Display plane B is now enabled and connected to Pipe B.
(II) I810(1): PIPEACONF is 0x80000000
(II) I810(1): PIPEBCONF is 0x80000000
(II) I810(1): Mode bandwidth is 47 Mpixel/s
(II) I810(1): maxBandwidth is 1088 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(1): Backing store disabled
(==) I810(1): Silken mouse enabled
(II) I810(1): Initializing HW Cursor
(**) Option "dpms"
(**) I810(1): DPMS enabled
(II) I810(1): direct rendering: Disabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
AUDIT: Thu Sep 28 16:57:46 2006: 7453 X: client 25 rejected from local host
AUDIT: Thu Sep 28 16:57:46 2006: 7453 X: client 25 rejected from local host
AUDIT: Thu Sep 28 16:58:30 2006: 7453 X: client 25 rejected from local host
AUDIT: Thu Sep 28 16:58:30 2006: 7453 X: client 25 rejected from local host
AUDIT: Thu Sep 28 16:58:30 2006: 7453 X: client 25 rejected from local host

```

I know I would have given up if it wasn't for the fact that I can see
```
(II) I810(1): Internal LCD: Using default hsync range of 30.00-70.00 kHz
(II) I810(1): Internal LCD: Using vrefresh range of 50.00-160.00 Hz
(II) I810(1): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) I810(1): Not using built-in mode "1152x864" (width too large for virtual size)
(--) I810(1): Virtual size is 1024x768 (pitch 1024)
(**) I810(1): *Built-in mode "1024x768"
```

for the LCD screen but
```
(II) I810(0): External Monitor: Using hsync range of 30.00-70.00 kHz
(II) I810(0): External Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
```

what is going on?!?
not only that my Vref for the CRT is set to 50-100 but it shows 50-160 and for the LCD i made it 60-60 but it still says 50-160?!?
Am I doing something completely wrong or something? None of the values seem to get applied for the correct screen.  Driving me crazy.

---

### Post by Monkus on 2006-09-28
Barak,
I think it has something to do with this particular chip. I have the same one you do and no matter what I do, I cannot get it to go the the resolution I had in XP. My Xorg.0.log says "no mode of this size" or so and when I use 915resolution, it just makes the Desktop so large I have to scroll to see it all (it goes off screen). I have been working on this for days now and cannot figure it out. I have tried so many things I hardly remember what I've done to the machine. But, I am a stubborn ba**ard and will probably not give up until I get it figured out. Let's keep talkin.

On a side note, that is the reason I am liking Ubuntu so much. There are those that say the internet and computer revolution is separating people from each other and making them more isolated. That is unless you look to things like Ubuntu. I have recieved a great deal of help and seen many examples of good teamwork, through this forum. The idea of a community based system seems to rectify any isolation that the computer age has implimented. Anyway, I digress.....

---

### Post by MonsterDog on 2006-09-28
Hi All,

I had to play around to get the right resolution on my Dell, too.  I don't have a solution for you, but I do have a couple of thoughts on the issue.

Monkus:  If I'm right you didn't actually run 915resolution because your bios allready reports the correct resolution.  It looks like your system is still convinced the res is 1024x768 so it gives you a bigger desktop than your screen can show.  What happens if you actually run 915resolution and change the 1024x768 resolution to 1280x800?

sudo 915resolution 38 1280 800 

should change the bios settings for all the color depths that were 1024x768 to 1280x800.  Then ctl-alt-bkspc and log in again.  Hopefully you can choose the right resolution at this point.  If that works for you, you have to figure out how to load it at startup.  There might be an issue with having 2 1280x800 vbios settings.  If that's true then change the original 1280x800 settings to something else.

man update-rc.d

Should give you an idea of how to load it at start-up.  If that doesn't explode your brain and you still need help, I'll see if I can remember how I did it.

---

### Post by barak on 2006-09-28
I switched which device was screen 0 and 1 in Xorg.conf - hoping that instead of applying the 1152x864 to the LCD it attempted to set the CRT or something - but in the log neither screen could apply 1152x864 - no built-in mode found - and the LCD displayed as 800x600 - and the option to select 1024x768 had gone from the menu.
I am getting used to the 1024x768... but surely this can be done.  I can customize almost anything in this OS - except which vga pipe the 1152x864 is detected on.  Maybe I should just upgrade the LCD monitor?!? is that even possible? he he he. Ahhhhh.... Damn it!

---

### Post by Monkus on 2006-09-28
MonsterDog,
Hey thanks for the ideas, but unfortunately they did the exact same thing. I think I'm gonna try and install the i810 and i915 snapshots and see what that does. I tried it earlier but it needs some kernel headers and such. I'll let ya know.

---

### Post by Monkus on 2006-09-29
Ok, I am tired of having this mess up my head. I switched to the "vesa" driver and it works in 1280x800 now. I have heard that the "vesa" driver is not as good, but hell, it works right. Anyway, if anyone figues anything out  please Post and let us know.

---

### Post by n0dl on 2006-09-30
When I first got my laptop two weeks ago, Dell inspiron 6400, I had the same trouble you had. No matter what I did, editing the /etc/defaults/915resolution script, patching vbios, and editing my xorg.conf i seemed to stay stuck in 1024x768. BUT! After two days of wadding through documents on ubuntu wiki, various guides and cunning i was able to set my resolution to 1280x800 with clear, crisp looking fonts and all! So without further a due I shall tell you of my fix.
915resolution -l lists all the modes *SUPPORTED* by your card, not all the modes read by xorg. I first noticed this when I tried 915resolution on mode 5c, a 32 bit 1920 x 1440 and patch it to 1680 x 1050. When I ran
```
sudo resolution 5c 1680 1050 32
```
then added the ForceBios statement as well as Mode "1680x1050" under the Depth 24 subsection then I started X and to no avail. So i opened up a terminal while X was running and read /var/log/Xorg.0.log. As I scrolled down I noticed the modes that were mentioned by 915resolution -l. When i got to the section Mode: 5c I saw that all the feilds following it were set to the value 0. On the contrary, the other modes had nonzero values in their fields. So I decided to do a test. I located the highest color depth that matched my 915resolution -l output (which was 16) and decided to patch the mode accordingly. The mode I decided was 45 and ran the following
```
sudo 915resolution 45 1280 1050 16
```
then changed the Force BIOS statement to 1280x800=1024x768. Then I restarted X and viola it worked! The only other discrepancy I had was that the fonts were still a little fuzzy. But I fixed that too! I read about dpi and how it works. Basically it stands for dots per inch and should be adjusted according to your display. Since Wide screen displays are an abnormality the dpi isnt standard like 96 or 100. Instead the dpi should be around 114. So the command startx -- -dpi 114 set my dpi to 114 and thus, my fonts are clear and crisp :)
The final steps i took was to edit the /etc/default/915resolution file to make the setting permanent and created ~/.Xresources file with the following line in it
```
Xft.dpi 114
```
which basically passes the option -- -dpi 114 automatically whenever i type startx.
Well I hoped that helped :)

---

### Post by Monkus on 2006-09-30
Man, you had me all excited and full of hope. 

Again, smashed to the rocks below. lol

I tried your idea, I found the entry in Xorg.0.log and reset my perameters to correspond to that information. Yet, I still get the scrolling desktop. Although I may try your dpi 114 idea. I could perhaps live with the 1024x768 if I could sharpen up the fonts. Thanks for your ideas. I think my best bet would be to find someone with the same machine, but I have had no luck with that, as of yet. I will keep trying.

---

### Post by penvzila on 2006-10-04
I have this problem too.  It isn't that the system won't display 1280x800, it's that it THINKS it is displaying it, but in reality you get this scrolling bullshit.

---

### Post by Monkus on 2006-10-04
Makes ya crazy don't it.

---

### Post by penvzila on 2006-10-06
The good thing is things like this usually get fixed pretty quickly.  I guess I'll use the vesa driver for now.

---

