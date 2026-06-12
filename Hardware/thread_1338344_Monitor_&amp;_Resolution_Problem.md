---
title: "Monitor &amp; Resolution Problem"
date: 2009-11-26
forum: Hardware
---

### Post by marsdend on 2009-11-26
Hi all, Please can you help me with a little problem?

I have **Ubuntu 9.10** installed on the PC and the maximum resolution i can get is 1280 x 1024 5:4. This is leaving the display not very clear.

**My Monitor**
Edge 10 - TW190
16 x 9
WXGA 1440 x 900
Contrast Ratio 500:1

**LSPCI Output**
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:03.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

Any help would be appreciated,
Thanks,
Dan

---

### Post by Grenage on 2009-11-26
You can manually specify the settings in xorg.conf:

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV [GeForce]"
    Monitor        "TW190"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1400x900_75.00"
    EndSubSection
EndSection
```

Obviously details will need to be correct.


EDIT: Actually, does Ubuntu use xorg.conf any more?

---

### Post by marsdend on 2009-11-26
> **Grenage said:**
> You can manually specify the settings in xorg.conf:

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV [GeForce]"
    Monitor        "TW190"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1400x900_75.00"
    EndSubSection
EndSection
```

Obviously details will need to be correct.

Ok, Please can you explain how do do this, ive heard about it but not sure how to actually do it?

Thanks for your reply,
Dan

---

### Post by marsdend on 2009-11-26
Just reading on the net, i think they have got rid of it in 9.10.

---

### Post by marsdend on 2009-11-26
any ideas?

---

### Post by Grenage on 2009-11-26
I assume it will still be used IF there is a config for it, so lets work on that assumption.

/etc/X11/xorg.conf - on my 9.10 it shows:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

I presume you would need to change it to (in bold):

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
[B]        SubSection "Display"
        Modes      "1400x900_75.00"[/B]

EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

Then restart X or just reboot and check your display options.  In my example, res 1400x900 at 75Mhz.

---

### Post by marsdend on 2009-11-26
> **Grenage said:**
> I assume it will still be used IF there is a config for it, so lets work on that assumption.

/etc/X11/xorg.conf - on my 9.10 it shows:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

I presume you would need to change it to (in bold):

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
[B]        SubSection "Display"
        Modes      "1400x900_75.00"[/B]

EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

Then restart X or just reboot and check your display options.  In my example, res 1400x900 at 75Mhz.

There is no xorg.conf file in that folder?

---

### Post by Grenage on 2009-11-26
P.S: There is a great guide here by heimo:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Grenage on 2009-11-26
> **marsdend said:**
> There is no xorg.conf file in that folder?

Ok, that's odd.  I have one here and it's a default install.

---

### Post by marsdend on 2009-11-26
> **Grenage said:**
> Ok, that's odd.  I have one here and it's a default install.

I manually went through the file browser if i type:
sudo nano /etc/X11/xorg.conf in terminal it just brings up a blank page with nothing on and few options. Any help to you?

---

### Post by Grenage on 2009-11-26
This is just a guess, but I have to assume your install simply doesn't have one because it hasn't needed one.  If you create one, it will most likely use it.

---

### Post by marsdend on 2009-11-26
> **Grenage said:**
> This is just a guess, but I have to assume your install simply doesn't have one because it hasn't needed one.  If you create one, it will most likely use it.

Is there any way of doing that? Creating on manually to use?

---

### Post by Grenage on 2009-11-26
When you tried to open it in nano and you got a blank screen, it created a new document with that name because it couldn't find it.  Doing the same thing and simply saving the file should do it for you.

---

### Post by marsdend on 2009-11-26
> **Grenage said:**
> When you tried to open it in nano and you got a blank screen, it created a new document with that name because it couldn't find it.  Doing the same thing and simply saving the file should do it for you.

ok, do i just paste:

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        SubSection "Display"
        Modes      "1400x900_75.00"

EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

and how do i save it?

---

### Post by Grenage on 2009-11-26
No No, you don't have an Nvidia card, so the settings will be different for you.  When I get home I will see if I can jot you something down.

---

### Post by marsdend on 2009-11-26
> **Grenage said:**
> No No, you don't have an Nvidia card, so the settings will be different for you.  When I get home I will see if I can jot you something down.

Ok, Much appreciated, if its possible could you explain how to do it step by step, 

Thanks again,
Dan

---

### Post by Grenage on 2009-11-26
Try the info below; copy it into your editor of choice and save it as xorg.conf in /etc/X11

```
Section "Device"
	Identifier	"Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"TW190"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Monitor "TW190"
	SubSection "Display"
		depth 24
		Modes "1400x900@75.00"
	EndSubSection
EndSection
```

I've not touched this stuff in a while, so I apologise if your computer explodes ;)  If you do get problems, just delete the file or empty it.

---

### Post by marsdend on 2009-11-26
> **Grenage said:**
> Try the info below; copy it into your editor of choice and save it as xorg.conf in /etc/X11

```
Section "Device"
	Identifier	"Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"TW190"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Monitor "TW190"
	SubSection "Display"
		depth 24
		Modes "1400x900@75.00"
	EndSubSection
EndSection
```

I've not touched this stuff in a while, so I apologise if your computer explodes ;)  If you do get problems, just delete the file or empty it.

I have tried it and it boots into command line with the command line login and this just flashes and wont let me type, sorry. Any other ideas, Is 9.10 bad for graphics, would going back a version help or not?

---

### Post by Grenage on 2009-11-26
Hi there,

9.10 is fine for graphics; at least, I haven't heard of any issues in particular.  It's most likely a bad xorg.conf, I'll see try and come up with something else unless someone else chimes in.

Gren.

---

### Post by randyist on 2009-11-26
I am having a similar problem. I have a new DCL LCD 20" Display running on a Dell Inspiron 530S Desktop.

My resolution is so low that it gives me a headache 1280 X 1024 is not the right ratio and it throws me off.

My resolution worked perfectly in 9.04 .. everything is so nice in 9.10 that I want to keep it, but I can't if this display can't be fixed. I was wondering if you could help me write an Xorg file or is it worth while?

Thank you.

---

### Post by Grenage on 2009-11-27
**Marsdend**: I cannot find any information on your monitor's display range, so can you do the following:

sudo apt-get install xresprobe
sudo ddcprobe

That 'should' display a mass of information, including a parameter called *monitorrange*.  If it doesn't, run ddcprobe a few more times (apparently it sometimes does that).  Assuming the info is displayed, paste it in here.

**randyist**: You might as well do the same thing, but also post the output of *lspci*.

---

### Post by ted_001 on 2009-11-27
I have the same problem.  There is no xorg.conf file to edit anywhere in the file system.  I have a nvidia card.  I have used system/hardware drivers to try to download the latest nvidia driver, but the download just hangs.
Ted

---

### Post by Grenage on 2009-11-27
Hi ted_001,

It's probably worth starting another thread on your issue, I imagine yours will simply be a case of getting the nvidia drivers going.

---

### Post by randyist on 2009-11-27
> **Grenage said:**
> **Marsdend**: I cannot find any information on your monitor's display range, so can you do the following:

sudo apt-get install xresprobe
sudo ddcprobe

That 'should' display a mass of information, including a parameter called *monitorrange*.  If it doesn't, run ddcprobe a few more times (apparently it sometimes does that).  Assuming the info is displayed, paste it in here.

**randyist**: You might as well do the same thing, but also post the output of *lspci*.
Ok, thanks. Here is the xresprobe result:

randy@randy-desktop:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)Q33/Q35/G33 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Q33/Q35/G33 Graphics Controller Hardware Version 0.0
memory: 8128kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 2095
eisa: DCL2095
serial: 000001a2
manufacture: 49 2008
input: composite sync, sync on green, analog signal.
screensize: 43 27
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1152x864@60
ctiming: 1280x960@60
ctiming: 1440x1440@60
ctiming: 1680x1680@60
ctiming: 1280x800@75
ctiming: 1280x1280@75
ctiming: 1280x960@75
ctiming: 1680x1680@75
dtiming: 1680x1050@59
monitorrange: 30-85, 56-76
monitorname: DCLCD
monitorname: DCL20AT

---------------------------Here is the LSPCI result:
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
---------------------------------Again, Thank you for your time.--------------------

---

### Post by Grenage on 2009-11-27
**randyist**: Did you used to use 1680x1050 or 1280x720?

---

### Post by Grenage on 2009-11-27
**randyist**:

Make a backup of your current xorg.conf, then overwrite it with this information:

```
Section "Monitor"
Identifier "Monitor0"
VendorName "DCLLCD"
ModelName "DCL20A"
HorizSync 65.29 - 65.29
VertRefresh 59.95 - 59.95
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82G33/G33"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1680x1050"
EndSubSection
EndSection
```

If that doesn't work, change the *device* section to:

```
Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82G33/G33"
BusID "PCI:0:2:0"
EndSection
```

The refresh rate will be hard-coded in the above config (that's your max refresh at that res).

---

### Post by randyist on 2009-11-27
Hi. Yes. it is 1680 X 1050 ..I will try this in just a moment and report back to you.

---

### Post by randyist on 2009-11-27
Unfortunately, it didn't work. I tried both ways and said that x failed to start or something like that.. so I deleted the xorg.conf file and i'm back to my old resolution again.

This is pretty tricky.

---

### Post by Grenage on 2009-11-27
Are you using a DVI or a VGA cable?

---

### Post by randyist on 2009-11-27
> **grenage said:**
> are you using a dvi or a vga cable?

vga.

---

### Post by Grenage on 2009-11-27
Try this:

```
Section "Monitor"
Identifier "Monitor0"
VendorName "DCLLCD"
ModelName "DCL20A"
HorizSync 24 - 82
VertRefresh 50 - 75
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82G33/G33"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 24
Modes "1680x1050"
EndSubSection
EndSection
```

Changed vert and hor to match manufacturer's information:

[http://www.dclcd.com/Products/LCD/Specs/spec_dcl20a.htm](http://www.dclcd.com/Products/LCD/Specs/spec_dcl20a.htm)

---

### Post by randyist on 2009-11-27
Ok. It loads up now without crashing Xserver, but the Maximum resolution is still 1280X1024... seems like we're getting closer though because Xserver loads with this configuration, still the same resolution though.

---

### Post by Grenage on 2009-11-27
```
Depth 24
```

If you change this to:

```
Depth 16
```

Does it help?

What I find odd is that from your ddcprobe:

```
oem: Intel(r)Q33/Q35/G33 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Q33/Q35/G33 Graphics Controller Hardware Version 0.0
memory: 8128kb
[B]mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m[/B]
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
```

It seems to think that your card might have a max res of 1280x1024.

---

### Post by randyist on 2009-11-27
no luck :(

the resolution worked perfectly in 9.04 .. I wonder if it has to do with the Kernel or with the xserver changes in 9.10

---

### Post by Grenage on 2009-11-27
Not a clue to be honest.  I'm shattered and off to bed, but I'll have a dig around for you in the morning!

---

### Post by randyist on 2009-11-27
Thank you. Either way, I appreciate you taking the time!

---

### Post by Grenage on 2009-11-27
This is a long shot, but if you go to the following thread and look at the last post:

[http://ubuntuforums.org/showthread.php?t=1308745](http://ubuntuforums.org/showthread.php?t=1308745)

Does that make any difference for you?

---

### Post by randyist on 2009-11-27
I'm unable to try it because I'm too much of a noob and Don't know how to Edit Grub 2 .. It's very difficult because there is no menu.lst  . . it's all separate files under the grub.d directory that I don't understand.. is there a way that I could install the old grub?

---

### Post by randyist on 2009-11-27
Ok. Update. Still not working. I uninstalled Grub 2 and installed Grub Legacy. I edited the menu.lst file in grub just like the guy did in that other post. It still doesn't seem to work. Perhaps ubuntu 9.10 just doesn't work on many systems. I've installed it on 3 laptops and it works perfectly. It seems to have trouble on a lot of these intel DELL computers, especially mine.

I hope a kernal update or something (I'm a noob and don't know how video is affected) will fix this problem because I really wish I could use 9.10 like many others.

---

### Post by Grenage on 2009-11-27
I know, it's really off.  The forum is full of 9.10 issues on intel cards; I never realised how many until I started searching for things with you.

---

### Post by randyist on 2009-11-27
I see. Well, I do appreciate you taking the time to help work on this issue. Thanks again!

---

### Post by Grenage on 2009-11-30
```

Section "Monitor"
Identifier "Monitor0"
VendorName "DCLLCD"
ModelName "DCL20A"
HorizSync 24 - 82
VertRefresh 50 - 75
Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82G33/G33"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 24
Modes "1680x1050"
EndSubSection
EndSection
```

Try this?

---

### Post by randyist on 2009-11-30
You are a GENIUS ! IT works!!!! Thank you so much!

So for the record, you have fixed a Inspiron 530s on a DCL LCD 20" Monitor!

Thanks again. you are a life saver!

---

### Post by Grenage on 2009-11-30
Wow, that's great news! MetaModes for the win!

---

### Post by randyist on 2009-11-30
I wish I knew what a Metamode was, LOL. I really need to learn about linux. So many people seem really good at it, and I don't know much more than ls -la  haha.

---

### Post by panos_p on 2009-12-01
hi all

same problem here, more or less
ubuntu 9.10 on ASUS P5KPL-AM with 
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

only two low resolution modes available:
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9  

i have tried to modify xorg.conf repeatedly :


Section "Monitor"
    Identifier   "Monitor0"
        HorizSync     31-81                   **# (taken from monitor's manual)**
        VertRefresh   56-75
    VendorName   "Monitor Vendor"
    ModelName    "A17-2"
        Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes "1024x768" 
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes "1024x768" 
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes "1024x768" 
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes "1024x768" 
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes "1024x768" 
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes "1024x768" 
    EndSubSection
EndSection


any suggestions???

thanx!

---

### Post by Grenage on 2009-12-01
Try this:

```
Section "Monitor"
Identifier "Monitor0"
VendorName "generic"
ModelName "unknown"
HorizSync 31 - 81
VertRefresh 56 - 75
Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82G33/G33"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection
```

---

### Post by panos_p on 2009-12-01
:( 
same situation 
only 2 modes available: 
800x600        60.3* 
640x480        59.9  

file xorg.conf looks like this: 

-------------------------------------------------------
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "extmod"
    Load  "record"
    Load  "glx"
    Load  "dbe"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
        VendorName "generic"
        ModelName "unknown"
        HorizSync     31 - 81
        VertRefresh   56 - 75    
        Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
Arch Linux Forums

Discussion forums for Arch Linux, a simple, lightweight linux distribution.

    * Download
    * AUR
    * Bugs
    * Wiki
    * Forums
    * Home

Arch Linux Forums

Discussion forums for Arch Linux, a simple, lightweight linux distribution.

    * Download
    * AUR
    * Bugs
    * Wiki
    * Forums
    * Home

    * Index
    * User list
    * Search
    * Register
    * LoginDriver "intel"

    * Index
    * User list
    * Search
    * Register
    * Login

        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82G33/G31 Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Arch Linux Forums

Discussion forums for Arch Linux, a simple, lightweight linux distribution.

    * Download
    * AUR
    * Bugs
    * Wiki
    * Forums
    * Home

    * Index
    * User list
    * Search
    * Register
    * Login

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
        DefaultDepth 16
    SubSection "Display"
    Depth 24
        Modes "1024x768"
        EndSubSection
EndSection

--------------------------------------------

any ideas?

thanx very much for the reply !!!

---

### Post by Grenage on 2009-12-01
Copy that xorg.conf as a backup:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.old
```

Then replace the whole lot with just the example I gave:

```
Section "Monitor"
Identifier "Monitor0"
VendorName "generic"
ModelName "unknown"
HorizSync 31 - 81
VertRefresh 56 - 75
Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82G33/G33"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
EndSection
```

Let's keep it simple and work from there. :)

---

### Post by panos_p on 2009-12-02
Simplicity worked out fine :)

[]("http://ubuntuforums.org/member.php?u=263074")Grenage,  thank you very much !!

---

### Post by Grenage on 2009-12-02
Glad it worked :)

---

