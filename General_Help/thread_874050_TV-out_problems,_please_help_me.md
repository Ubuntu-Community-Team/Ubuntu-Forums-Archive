---
title: "TV-out problems, please help me"
date: 2008-07-29
forum: General Help
---

### Post by ericus on 2008-07-29
Okay, here is the problem. I have connected my old TV via 9-pin S-video to a 5-pin s-video adapter, and then to a scart-adapter. When I turn on my computer both the TV and screen works, except that the TV runs in black&white.

 Just before I get to the login screen the TV goes black, and the computer screen says "No signal" for a second and then the image gets back, but the TV remains black. If I shut off the computer monitor before this happens then the TV works, but in B/W and 800x600. I can then turn on the computer screen, and it is also in 800x600 mode, without a possibility of change.

Can anyone please help me with this? My friends just keep saying that linux sucks, and I wanna prove them that they're wrong. 

Here is some info:
ATI Radeon 9550 card with drivers installed with envy-ng.
Running Ubunty Hardy Heron
My Xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" Above "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnableMonitor" "crt2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVStandard" "PAL-G"
	Option	    "TVFormat" "PAL-G"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

fglrxinfo:```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.1.7659 Release
```

Thanks in advance,
Eric

---

### Post by onesojourner on 2008-07-29
> **ericus said:**
> Okay, here is the problem. I have connected my old TV via 9-pin S-video to a 5-pin s-video adapter, and then to a scart-adapter. When I turn on my computer both the TV and screen works, except that the TV runs in black&white.

 Just before I get to the login screen the TV goes black, and the computer screen says "No signal" for a second and then the image gets back, but the TV remains black. If I shut off the computer monitor before this happens then the TV works, but in B/W and 800x600. I can then turn on the computer screen, and it is also in 800x600 mode, without a possibility of change.

Can anyone please help me with this? My friends just keep saying that linux sucks, and I wanna prove them that they're wrong. 

Here is some info:
ATI Radeon 9550 card with drivers installed with envy-ng.
Running Ubunty Hardy Heron
My Xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" Above "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnableMonitor" "crt2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVStandard" "PAL-G"
	Option	    "TVFormat" "PAL-G"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

fglrxinfo:```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.1.7659 Release
```

Thanks in advance,
Eric


This may help you.
[http://ubuntuforums.org/showthread.php?p=5484100#post5484100](http://ubuntuforums.org/showthread.php?p=5484100#post5484100)

 I think if you add theses lines it will do the same thing. Add them under your screen section.
    Option         "TVStandard" "NTSC-M"
    Option         "TVOutFormat" "SVIDEO"

---

### Post by ericus on 2008-07-29
> **onesojourner said:**
> This may help you.
[http://ubuntuforums.org/showthread.php?p=5484100#post5484100](http://ubuntuforums.org/showthread.php?p=5484100#post5484100)

 I think if you add theses lines it will do the same thing. Add them under your screen section.
    Option         "TVStandard" "NTSC-M"
    Option         "TVOutFormat" "SVIDEO"

Thank you.

But the thing now is that I dont get any picture at all on my TV. Just before the login screen it turns black. What to do? :( How can I enable the TV-out? Ubuntu doesnt seem to find the TV.

---

### Post by wootah on 2008-07-29
Check my sig about the TV stuff. I have a guide on this for ATI cards :)

When you go to login (leave your tv and monitor on) but in the session selection, select the GNOME session and not default. You should have to do this just once. See if that fixes it.

Next, you are going to want to read up on **xrandr**. You can use this to setup your monitor (and tv) and write the configuration to the xorg.conf. I suggest skimming the man pages and then checking [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) .

Good luck :)

---

### Post by ericus on 2008-07-29
> **wootah said:**
> Check my sig about the TV stuff. I have a guide on this for ATI cards :)

When you go to login (leave your tv and monitor on) but in the session selection, select the GNOME session and not default. You should have to do this just once. See if that fixes it.

Next, you are going to want to read up on **xrandr**. You can use this to setup your monitor (and tv) and write the configuration to the xorg.conf. I suggest skimming the man pages and then checking [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) .

Good luck :)

Hi, and thanks for taking your time!

I'm sorry to say that choosing GNOME didnt help at all. Just to clarify, the TV goes black a while before the login screen.

```
ericus@ericus-desktop:~$ aticonfig --query-monitor
  Connected monitors: crt1
  Enabled monitors: crt1
```

I'm getting so tired of messing around with this :(

---

### Post by onesojourner on 2008-07-29
> **ericus said:**
> Thank you.

But the thing now is that I dont get any picture at all on my TV. Just before the login screen it turns black. What to do? :( How can I enable the TV-out? Ubuntu doesnt seem to find the TV.


You should be able to restore your last settings:

```
cd /etc/X11/
sudo cp xorg.backup xorg.conf
```

---

### Post by ericus on 2008-07-29
> **onesojourner said:**
> You should be able to restore your last settings:

```
cd /etc/X11/
sudo cp xorg.backup xorg.conf
```

Yes, I did that, but whatever I do the TV turns black just before the login screen, I dont get it...

---

### Post by ericus on 2008-07-29
OK, now I can boot and both screens are enables, but TV's still b/w and both has 800x600 as resolution. Ubuntu says that it's running in low graphics mode. Here is my xorg.conf now:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "LCD" 0 0
	Screen         "Default Screen" 0 0
	Screen         "TV" LeftOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor (Screen 0)"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1] (Screen 1)"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device (Screen 0)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnableMonitor" "crt2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1] (Screen 1)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVFormat" "PAL-B"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "LCD"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "TV"
	Device     "aticonfig-Device[1] (Screen 1)"
	Monitor    "aticonfig-Monitor[1] (Screen 1)"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

And here is another output if that helps:
```
ericus@ericus-desktop:~$ aticonfig --query-monitor
Data incomplete in file /etc/X11/xorg.conf
	Undefined Screen "Default Screen" referenced by ServerLayout "Default Layout".
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.
```

---

### Post by wootah on 2008-07-29
> **ericus said:**
> Hi, and thanks for taking your time!

I'm sorry to say that choosing GNOME didnt help at all. Just to clarify, the TV goes black a while before the login screen.

```
ericus@ericus-desktop:~$ aticonfig --query-monitor
  Connected monitors: crt1
  Enabled monitors: crt1
```I'm getting so tired of messing around with this :(

Yeah, so it sounds like it is using the wrong video encoding for your region/tv. Are you in North America? You'll need NTSC/M.

Did you check the link about ATI cards in my sig?

Unfortunately I have had nothing but trouble with ATI cards. This stuff is a lot easier with nVidia products (in my experience). Luckily, I'm starting to discover all the little details of how the graphical system works with X, so things are getting better/easier.

---

### Post by warp99 on 2008-07-29
(Deleted, wrong thread)

---

### Post by ericus on 2008-07-29
> **wootah said:**
> Yeah, so it sounds like it is using the wrong video encoding for your region/tv. Are you in North America? You'll need NTSC/M.

Did you check the link about ATI cards in my sig?

Unfortunately I have had nothing but trouble with ATI cards. This stuff is a lot easier with nVidia products (in my experience). Luckily, I'm starting to discover all the little details of how the graphical system works with X, so things are getting better/easier.
I am from Sweden. PAL-B is standard here.
Can you see any errors in my xorg.conf?

The thing I want to fix the most right now is the resolution, I cant stand 8000x600 on my computer screen. I know that the TV might not work with higher resolution, so how do I do this? :(

---

### Post by ericus on 2008-07-30
Anyone who might know why it wont work when my driver are loaded? Only in low graphics mode, in 800x600 b/w. Seems to **** up my xserver or something.

---

### Post by wootah on 2008-08-01
> **ericus said:**
> Anyone who might know why it wont work when my driver are loaded? Only in low graphics mode, in 800x600 b/w. Seems to **** up my xserver or something.

Looks like you might need a modeline for your LCD monitor... unless you know what it is, do the following:

```

sudo apt-get install read-edid
sudo get-edid | parse-edid

```You will get an output such as the following:

> 
Section "Monitor"
  # Block type: 2:0 3:fd
  # Block type: 2:0 3:fc
  Identifier "90GX2"
  VendorName "NEC"
  ModelName "90GX2"
  # Block type: 2:0 3:fd
  HorizSync 31-81
  VertRefresh 56-75
  # Max dot clock (video bandwidth) 140 MHz
  # Block type: 2:0 3:fc
  # Block type: 2:0 3:ff
  # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

  Mode    "1280x1024"     # vfreq 60.020Hz, hfreq 63.981kHz
  DotClock        108.000000
                    HTimings        1280 1328 1440 1688
    VTimings        1024 1025 1028 1066
    Flags   "+HSync" "+VSync"
  EndMode
  # Block type: 2:0 3:fd
  # Block type: 2:0 3:fc
  # Block type: 2:0 3:ff
EndSection
You can insert this into your monitor section of your xorg.conf file. This will give you the proper resolutions. After that, you should have a bigger resolution.

Let me know if that helps :)

PS: Please backup xorg.conf

---

