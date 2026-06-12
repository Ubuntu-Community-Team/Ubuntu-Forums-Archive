---
title: "Video Card Recommendation Request"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by Error_Msg on 2005-07-03
I run Hoary in an old but trusty PII 400Mh 256Mb RAM 10G HD with a 3dfx Voodoo Banshee. 
When I run glxgears I get an average of 100 FPS and a ton of libGL errors (3D driver doesn't support visual). 
I'm looking to replace it with something that will render 1000 FPS.
What are my options?
TIA

E_M

---

### Post by Yagisan on 2005-07-03
[QUOTE=Error_Msg]I run Hoary in an old but trusty PII 400Mh 256Mb RAM 10G HD with a 3dfx Voodoo Banshee. 
When I run glxgears I get an average of 100 FPS and a ton of libGL errors (3D driver doesn't support visual). 
I'm looking to replace it with something that will render 1000 FPS.
What are my options?
TIA

E_M[/QUOTE]
I'm not sure that is possible with your system, considering it's age. If you have an agp port that can take 4x agp cards (check the manual if you still have it) current budget/entry level nvidia cards would give you a boost, but then the bottleneck will be your cpu.

Looking in the glxgears benchmark thread [http://ubuntuforums.org/showthread.php?t=39349](http://ubuntuforums.org/showthread.php?t=39349) will give you an idea of relative performance.

What are you trying to play ?

---

### Post by Error_Msg on 2005-07-03
Thanks, I posted my current FPS in that thread.
I'll look into the nvidias (if it'll work, that is :grin: )

E_M

---

### Post by Yagisan on 2005-07-04
Error_Msg, I looked at your "error messages" in the benchmark thread. Those errors are because the voodoo cards only support **16bit** colour, not 32bit. Try setting your desktop to 16bit, and run glxgears again and see if you get a performance increase.

A word of warning about upgrading your machine. If your motherboard only supports AGP 2x, you will not be able to upgrade to a new AGP video card. AGP 2x slots supply power at 3.3 volts only, while 4x and 8x AGP cards require a lower 1.5 volt supply. Putting a 4x/8x card in a 2x slot will most likely damage the card, and that won't be covered under warranty.

---

### Post by darkpark on 2005-07-04
i don't know if they are still around somewhere nor their specs, but you could try looking for one of the newer 3dfx voodoo cards.  before they went under, i think they had a voodoo5 or something.  that might be a sufficient of an upgrade short of just completely replace your computer.

---

### Post by Error_Msg on 2005-07-04
[QUOTE=Yagisan]Error_Msg, I looked at your "error messages" in the benchmark thread. Those errors are because the voodoo cards only support **16bit** colour, not 32bit. Try setting your desktop to 16bit, and run glxgears again and see if you get a performance increase.

A word of warning about upgrading your machine. If your motherboard only supports AGP 2x, you will not be able to upgrade to a new AGP video card. AGP 2x slots supply power at 3.3 volts only, while 4x and 8x AGP cards require a lower 1.5 volt supply. Putting a 4x/8x card in a 2x slot will most likely damage the card, and that won't be covered under warranty.[/QUOTE]

Thanks for looking into it Yagi.
As our friend darkpark suggested, upgrading the Voodoo with a newer (still an antique) Voodoo seems like a good idea to me.
I found a Voodoo 2 Banshee in Ebay. The card is in England and right now is going for 2.70 (Euros I suppose. Did UK suscribe to the Euro thing or are they still pounds?) Anyway is less than U$D 5. I will pursue that one. Will see how high people will bid (what do they want it for, a museum?).
I found the driver with Synaptic too.
On the other hand, I am researching the voltage thing, and I found the spec sheet:
[http://support.gateway.com/s/VIDCARD/Creative/V00910/V0091008.shtml](http://support.gateway.com/s/VIDCARD/Creative/V00910/V0091008.shtml)
It says 9W. If I remember correctly W= Volts*Amps but I have no idea what the amps value is so I can't figure out the volts.
In the meantime, I order this one for U$D 20:
nVidia GeForce2 GTS NV15 / 32MB DDR / 4X , so even if I fry it is no biggie.
I read in one of the threads, I don't remember if in gaming or here, somebody saying that they installed a 4x card in a 2x board, and the only consequences there is that the card runs at 2x.
Like the blind man said, we'll see.
Isn't this fun?

E_M

---

### Post by Error_Msg on 2005-07-04
[QUOTE=darkpark]i don't know if they are still around somewhere nor their specs, but you could try looking for one of the newer 3dfx voodoo cards.  before they went under, i think they had a voodoo5 or something.  that might be a sufficient of an upgrade short of just completely replace your computer.[/QUOTE]

Thanks darkpark. That is a good idea. I'm looking into it.
Why would I replace the computer?! Is only seven years old. My TV is way older than that!

E_M

---

### Post by Yagisan on 2005-07-05
[QUOTE=Error_Msg]Thanks for looking into it Yagi.[/QUOTE]
No problem. Reminded me of when I used to be hardware technical support many years ago.

[QUOTE=Error_Msg]
In the meantime, I order this one for U$D 20:
nVidia GeForce2 GTS NV15 / 32MB DDR / 4X , so even if I fry it is no biggie.
I read in one of the threads, I don't remember if in gaming or here, somebody saying that they installed a 4x card in a 2x board, and the only consequences there is that the card runs at 2x.
Like the blind man said, we'll see.
Isn't this fun?

E_M[/QUOTE]
Yep sure is fun :) Older cards were 4x/2x/1x compatible (voltage and speedwise) and you may still find those available as 4x max speed cards, the newer 8x/4x cards are far more likely to be 1.5v models. I have a machine as old as yours (350Mhz k6/2) up and running still, it has outlasted 2 of my newer machines and still keeps going. The heat ended up killing newer machines, both burnt out :( and they weren't overclocked and came with the stock fan.

Goodluck with your new video cards (I prefer the geforce) and post your new scores in the glxgears thread.

---

### Post by Error_Msg on 2005-07-08
I installed the Geforce but I'm having config problems. 
I downladed and installed the drivers per:
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)
but when I run:
sudo nvidia-glx-config enable
and the xorg.conf gets edited, upon restarting the machine, X's gdm doesn't start so I have to revert to the pre nvidia-glx-config enable xorg.conf which I configured via dpkg-reconfigure xserver-xorg using auto detection (nv) and all the defaults.
Before I was getting 100 FPS when running glxgears with my ancient Voodoo Banshe, now I get:
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.
and
:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

So basically no 3D at all. 
Should I just toss the Geforce out the window? ](*,) 
TIA

E_M

---

### Post by celloandy on 2005-07-09
The nv driver doesn't support any 3D acceleration, to the best of my knowledge.  What error is X having when it dies with the nvidia driver?  Are you sure that the nvidia kernel module is loaded before X starts?

Andrew

---

### Post by Yagisan on 2005-07-09
[QUOTE=Error_Msg]
Should I just toss the Geforce out the window? ](*,) 
[/QUOTE]No. It does sound like a configuration error.

Could you first confirm that you have the following packages installed
linux-restricted-modules-*your-kernel-version* eg mine is linux-restricted-modules-amd64-generic
nvidia-glx
nvidia-kernel-common

Could you please post your
/etc/modules
/etc/X11/xorg.conf

Eg my /etc/modules looks like this```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

via82cxxx
sata_via
raid5
raid0
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
rtc
sbp2
sr_mod
nvidia
floppy

```
and my /etc/X11/xorg.conf looks like this```
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
#	Load	"dri"
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"	"true"
	Option		"RenderAccel"	"false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
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
You'll notice I have a line like this **#	Load	"dri"** in my xorg.conf that is something that is missing from the ubuntuguide.

---

### Post by Error_Msg on 2005-07-09
[QUOTE=celloandy]The nv driver doesn't support any 3D acceleration, to the best of my knowledge.  What error is X having when it dies with the nvidia driver?  Are you sure that the nvidia kernel module is loaded before X starts?

Andrew[/QUOTE]

No I'm not sure. I just followed the guide step by step.

E_M

---

### Post by mohaham on 2005-07-09
after installing nvidia drivers..
have u edited /etc/X11/xorg.conf file
to replace "nv" with "nvidia" in this section

...
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
...

---

### Post by Error_Msg on 2005-07-09
[QUOTE=Yagisan]No. It does sound like a configuration error.

Could you first confirm that you have the following packages installed
linux-restricted-modules-*your-kernel-version* eg mine is linux-restricted-modules-amd64-generic
nvidia-glx
nvidia-kernel-common

Could you please post your
/etc/modules
/etc/X11/xorg.conf

Eg my /etc/modules looks like this```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

via82cxxx
sata_via
raid5
raid0
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
rtc
sbp2
sr_mod
nvidia
floppy

```
and my /etc/X11/xorg.conf looks like this```
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
#	Load	"dri"
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"	"true"
	Option		"RenderAccel"	"false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
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
You'll notice I have a line like this **#	Load	"dri"** in my xorg.conf that is something that is missing from the ubuntuguide.[/QUOTE]
 Yagi!
My /etc/modules:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

and my xorg.conf (I have edited this one many many times, and I tried commenting out the load dri line before, but this is the *working* one that I keep reverting to after failure)

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
	Identifier	"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"GATEWAY EV70"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Monitor		"GATEWAY EV70"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

You know, come to think of it, when downloading the drivers and settings the repositories gave me some kind of error but I just blew it off and kept on trucking.
Maybe I should uninstall the drivers and install them again.

E_M

---

### Post by Error_Msg on 2005-07-09
[QUOTE=celloandy]The nv driver doesn't support any 3D acceleration, to the best of my knowledge.  What error is X having when it dies with the nvidia driver?  Are you sure that the nvidia kernel module is loaded before X starts?

Andrew[/QUOTE]

I copied Yagi's settings, and this time I paid attention to the X fatal errors, I goes like this:
"The nvidia kernel module does not appear to be receiving interrupts generated by the nvidia graphics. Please see the FAQ in readme. Failed to initialize nvidia graphics device. Unload module nvidia." 
So you're right. The nvidia kernel module is not loading.
I will look for this readme. Where can I find it? I guess I will start in the nvidia folder.

E_M

---

### Post by Error_Msg on 2005-07-09
[QUOTE=mohaham]after installing nvidia drivers..
have u edited /etc/X11/xorg.conf file
to replace "nv" with "nvidia" in this section

...
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
...[/QUOTE]

Yes, I sure have. That's when it all goes to hell in a hand basket. :grin: 

E_M

---

### Post by Yagisan on 2005-07-09
[QUOTE=Error_Msg]I copied Yagi's settings, and this time I paid attention to the X fatal errors, I goes like this:
"The nvidia kernel module does not appear to be receiving interrupts generated by the nvidia graphics. Please see the FAQ in readme. Failed to initialize nvidia graphics device. Unload module nvidia." 
So you're right. The nvidia kernel module is not loading.
I will look for this readme. Where can I find it? I guess I will start in the nvidia folder.

E_M[/QUOTE]First, could you check in your BIOS if you have a setting that looks similar to **Allocate IRQ to VGA** if so, could you set that to yes and try again.

Could you also attach the output from /proc/interrupts

---

### Post by Error_Msg on 2005-07-09
[QUOTE=Yagisan]First, could you check in your BIOS if you have a setting that looks similar to **Allocate IRQ to VGA** if so, could you set that to yes and try again.

Could you also attach the output from /proc/interrupts[/QUOTE]

You know? It's interesting that you bring up this point, because I found this entry in /var/log/messages that I thought could be relevant:

Jul  8 19:55:32 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
Jul  8 19:55:32 localhost kernel: ** causes a device to stop working, it is probably because the
Jul  8 19:55:32 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
Jul  8 19:55:32 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
Jul  8 19:55:32 localhost kernel: ** behavior.  If this argument makes the device work again,
Jul  8 19:55:32 localhost kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
Jul  8 19:55:32 localhost kernel: ** so I can fix the driver.

If I would only know where that little argument goes!

This is the contents of /proc/interrupts:
           CPU0       
  0:    9950462          XT-PIC  timer
  1:       3684          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          0          XT-PIC  parport0
  8:          1          XT-PIC  rtc
  9:          0          XT-PIC  acpi, uhci_hcd
 10:       9465          XT-PIC  eth0
 11:        520          XT-PIC  Ensoniq AudioPCI
 12:     309422          XT-PIC  i8042
 14:     127612          XT-PIC  ide0
 15:      19854          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

Yagi, I'm going into the BIOS now.
If you don't hear from me in a couple of days, send the cavalry! :grin: 

E_M
Ps: BTW, I also found some entries saying that the signal was being converted to 2x!

---

### Post by Error_Msg on 2005-07-09
The only relevant setting I found in the BIOS was "Sharing of IRQs" which was set to "Auto" (minimize of IRQ sharings).
The other options were sharing of 1, 2, or 3, IRQ's, so I set it to 3, whattahell.
Tried again, X didn't start.
After an elapsed time of 10 hours of nvidia driver battling, I think that i has me beat. 

E_M

---

### Post by Error_Msg on 2005-07-10
Below are the legacy GPUs that are no longer supported in the unified nvidia driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.


    NVIDIA chip name                   Device PCI ID
    -------------------------------    -------------------------------
    RIVA TNT                           0x0020
    RIVA TNT2/TNT2 Pro                 0x0028
    RIVA TNT2 Ultra                    0x0029
    Vanta/Vanta LT                     0x002C
    RIVA TNT2 Model 64/Model 64 Pro    0x002D
    Aladdin TNT2                       0x00A0
    GeForce 256                        0x0100
    GeForce DDR                        0x0101
    Quadro                             0x0103
    GeForce2 GTS/GeForce2 Pro          0x0150 <<<<<<<<<<<<
    GeForce2 Ti                        0x0151
    GeForce2 Ultra                     0x0152
    Quadro2 Pro                        0x0153

Lesson: Do your homework *before* you shop. :grin: 
I did learn a lot of Linux in the process of trying to make this unsupported card work, and I also learnt that no matter how little you know, and how deep you go into Ubuntu you cannot break it, and if you do, you can certainly fix it. I did.

E_M

---

### Post by Yagisan on 2005-07-13
[QUOTE=Error_Msg]Below are the legacy GPUs that are no longer supported in the unified nvidia driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.


    NVIDIA chip name                   Device PCI ID
    -------------------------------    -------------------------------
    RIVA TNT                           0x0020
    RIVA TNT2/TNT2 Pro                 0x0028
    RIVA TNT2 Ultra                    0x0029
    Vanta/Vanta LT                     0x002C
    RIVA TNT2 Model 64/Model 64 Pro    0x002D
    Aladdin TNT2                       0x00A0
    GeForce 256                        0x0100
    GeForce DDR                        0x0101
    Quadro                             0x0103
    GeForce2 GTS/GeForce2 Pro          0x0150 <<<<<<<<<<<<
    GeForce2 Ti                        0x0151
    GeForce2 Ultra                     0x0152
    Quadro2 Pro                        0x0153

Lesson: Do your homework *before* you shop. :grin: 
I did learn a lot of Linux in the process of trying to make this unsupported card work, and I also learnt that no matter how little you know, and how deep you go into Ubuntu you cannot break it, and if you do, you can certainly fix it. I did.

E_M[/QUOTE]
E_M, that is only for the new 7667 drivers, 7174 which is what is in Ubuntu hoary does support your card. What drivers are you using ?

---

