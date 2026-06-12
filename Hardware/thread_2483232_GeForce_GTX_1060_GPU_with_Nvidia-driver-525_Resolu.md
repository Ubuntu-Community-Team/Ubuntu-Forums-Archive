---
title: "GeForce GTX 1060 GPU with Nvidia-driver-525 Resolutions Problem"
date: 2023-01-23
forum: Hardware
---

### Post by mark bower on 2023-01-23
System:  Ubuntu-Mate 20.04, ;Samsung 40” TV, native resolution 3840 x 2160 HDMI 2.0; GTX 1060, HDMI 2.0; cable “high speed”.

Ubuntu will not display 2560 x 1600 or 2560 x 1440 pixels on my TV monitor with Nvidia “nvidia-driver 525-distro non-free recommended” installed.  Software & Updates show this to be the correct driver to install.  I need to be able to switch between resolutions 3840 x 2160 and 2560 x 1600.

xrandr shows the resolutions are not available.  some other diagnostics:

```
mark@senior:~$ sudo lshw -c video
[sudo] password for mark: 
  *-display                 
       description: VGA compatible controller
       product: GP106 [GeForce GTX 1060 6GB]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:136 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff

mark@senior:~$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001C03sv00003842sd00006267bc03sc00i00
vendor   : NVIDIA Corporation
model    : GP106 [GeForce GTX 1060 6GB]
driver   : nvidia-driver-515 - distro non-free
driver   : nvidia-driver-525 - distro non-free recommended
driver   : nvidia-driver-515-server - distro non-free
driver   : nvidia-driver-525-server - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-510 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```
When I boot to Win10 or Win7 on the same PC, the 2560 x 1600 or 2560 x 1440 resolutions are available. 

Is there a way to get Linux to display the "missing resolutions" which Win10 and Win7 display?

---

### Post by TheFu on 2023-01-25
X/Windows 
or
Wayland?

Which DE - desktop environment - ah Mate.  Most DEs have a User's Guide which explains how to control the screen resolution.  Of course, if the TV doesn't work at the resolution + update speed, then it won't work.  Both are important.  The GPU shouldn't throw 2560 x 1600 @ 120Mhz to a TV that only supports 2560 x 1600 @ 30Mhz or 60Mhz.  I didn't look it up, but that's my best guess.

BTW, 'lxrandr' is a simple GUI to control what xrandr does. I think you'll like it, but it only works for X/Windows, not Wayland.
For Wayland, I don't know.

---

### Post by TheFu on 2023-01-25
If the TV isn't telling the GPU the resolutions are available, probably not a good idea to force it.  Is there any HDMI switch being used?  Sometimes those block the EDID information from the monitor getting to the GPU.

There are some edid* commands on Linux so show what the GPU is being told.  The data in the output from those commands can be used to create an xorg.conf  modeline.

---

### Post by mark bower on 2023-01-25
I will check tomorrow on Xorg vs Wayland - does it make a difference?  Mate:  System>Control Center>Displays is where I can see available resolutions as well as the command line cmds.  I have not set any HDMI switch as I do not know what/where it is.  I can only reiterate that Win10 and Win7 have no problem.

---

### Post by mark bower on 2023-01-26
The PC is using X11.  lxrandr is neat and shows the missing desired resolution:  2560 x 1600.  Any suggestions for a fix?

---

### Post by TheFu on 2023-01-26
> **mark bower said:**
> The PC is using X11.  lxrandr is neat and shows the missing desired resolution:  2560 x 1600.  Any suggestions for a fix?

Select the resolution you want and "Apply" then "Save".
Does that not work?

You can force the resolution to whatever you like using the automatic program running for your DE at login with something like this:
```
xrandr  --output VGA-1 --mode  1920x1200
xrandr  --output HDMI-1 --mode  1920x1080
```

You'll need to look up the specific output device and set the mode to match what 'xrandr' or 'lxrandr' sees to create the correct xrandr command.
There are all sorts of names, so don't expect yours to be like mine.  If lxrandr fixed it, then xrandr can too.

---

### Post by mark bower on 2023-01-27
```
Select the resolution you want and "Apply" then "Save"
```

I am not clear re your suggestion:  lxrandr does not show the needed resolution?  So desired resolution is not available to select and save?

```
You can force the resolution to whatever you like using the automatic program running for your DE at login with something like this:
```

Are you saying that I can make an added resolution, which will be permanently available (not lost on reboot), via cmd line such as,

"xrandr  --output HDMI-1 --mode  2560x1600" (the HDMI on the PC is in fact on HDMI-1)

---

### Post by TheFu on 2023-01-27
You said:
> **mark bower said:**
>  lxrandr is neat and shows the missing desired resolution:  2560 x 1600.  

So I took that to mean that the desired resolution was being showed, so it could be selected.  If that isn't the situation, you'll need to get the monitor to provide the available resolutions to your GPU.  That should happen automatically for VGA, HDMI, DP connections.


```
$ get-edid
``` will get the information from the monitor in a machine format.
```
$ parse-edid
``` can read the machine format and should output the supported resolutions and other technical information that can be used to create modelines for the xorg.conf file.

So, in theory, running 
```
$ sudo get-edid |parse-edid 
```
should show everything. That's the theory.  [https://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor](https://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor)


Here's a modeline from one of my systems:
```
        Modeline        "Mode 0" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync 
```
The output seems to create a full xorg.conf "Monitor"  section, which is really nice. I don't have nvidia working in any of my systems, so that's from an AMD GPU.  One of my AMD GPU systems is using VESA, not the proprietary driver. Only the proprietary driver is outputting useful information.

---

### Post by mark bower on 2023-01-27
"lxrandr is neat and shows the missing desired resolution: 2560 x 1600" - geez what terrible wording indeed - just the opposite of what I intended!!!!!!!!!!

So, following is the edid output.  
1)What do the numbers on a ModeLine mean?
2)Given the output, what is the next step aiming for the 2560x1400 display?

```
mark@senior:~$ sudo get-edid |parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
1 potential busses found: 4
256-byte EDID successfully retrieved from i2c bus 4
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
	Identifier "SAMSUNG"
	ModelName "SAMSUNG"
	VendorName "SAM"
	# Monitor Manufactured week 1 of 2016
	# EDID version 1.3
	# Digital Display
	DisplaySize 890 500
	Gamma 2.20
	Option "DPMS" "false"
	Horizsync 15-81
	VertRefresh 24-75
	# Maximum pixel clock is 300MHz
	#Not giving standard mode: 1152x864, 75Hz
	#Not giving standard mode: 1280x720, 60Hz
	#Not giving standard mode: 1280x800, 60Hz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1600x900, 60Hz
	#Not giving standard mode: 1680x1050, 60Hz

	#Extension block found. Parsing...
#WARNING: I may have missed a mode (CEA mode 95)
#DOUBLE WARNING: It's your first mode, too, so this may actually be important.
#WARNING: I may have missed a mode (CEA mode 93)
#WARNING: I may have missed a mode (CEA mode 94)
#WARNING: I may have missed a mode (CEA mode 98)
#WARNING: I may have missed a mode (CEA mode 99)
#WARNING: I may have missed a mode (CEA mode 100)
	Modeline 	"Mode 2" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 0" 297.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync 
	Modeline 	"Mode 1" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 3" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 4" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 5" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 6" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
	Modeline 	"Mode 7" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
	Modeline 	"Mode 8" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 9" 74.250 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 10" 74.250 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 11" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
	Modeline 	"Mode 12" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
	Modeline 	"Mode 13" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 14" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 15" 74.25 1920 2448 2492 2640 540 542 547 562 +hsync +vsync interlace
	Modeline 	"Mode 16" 85.50 1366 1436 1579 1792 768 771 774 798 +hsync +vsync 
	Option "PreferredMode" "Mode 2"
EndSection
```

---

### Post by TheFu on 2023-01-28
> **mark bower said:**
> "lxrandr is neat and shows the missing desired resolution: 2560 x 1600" - geez what terrible wording indeed - just the opposite of what I intended!!!!!!!!!!

So, following is the edid output.  
1)What do the numbers on a ModeLine mean?
2)Given the output, what is the next step aiming for the 2560x1400 display?


They are what the monitor says it can support.  There are 16 modes available.  It is odd that the resolution isn't used vs "Mode 1".  Seems like a mistake in the TV firmware to me.  The fact that the exact TV model isn't listed in the EDID is odd too. I've never seen that either.  You can replace those comments with anything you like.  I'd put the resolutions into there.

BTW, the errors say some modes were missed, so perhaps running the command a few times to see if other, desired modes show up would be a good idea.

If it were me, I'd take the Monitor section information, create a text file with everything from Section ---> EndSection, including both of those lines.  Then I'd move that file to /etc/X11/xorg.conf.d/ and 'chown root:root' on it with 644 permissions.  Then I'd reboot.

BTW, the monitor is NOT reporting support for the resolution you want, so asking for it means some sort of scaling is happening.

1920x2008 at 148.500hz updates seems to be the native resolution based on the output above.

When you look in the monitor manual, it should list all the resolutions and update frequencies.  That would be important.  In theory, monitors since around 2000 have protections to prevent over driving them, but just a few months ago, I recall reading where some monitors were destroyed by a GPU driving it beyond the capabilities.  The EDID should say correctly the capabilities of the connected monitor. If it doesn't, I'd suspect a bad/weak cable.

---

### Post by mark bower on 2023-01-28
```
mark@senior:~$ sudo get-edid |parse-edid
```
I ran the above code again get the same outputs.

BUT, this discussion seems to focus on the TV(monitor).  What about my first post?
```
When I boot to Win10 or Win7 on the same PC, the 2560 x 1600 or 2560 x 1440 resolutions are available. 
```
Windows acesses the resolution(s) I need.  Doesn't this imply that the Nvidia supplied driver for Ubuntu is the issue?

---

### Post by TheFu on 2023-01-28
> **mark bower said:**
>  Windows acesses the resolution(s) I need.  Doesn't this imply that the Nvidia supplied driver for Ubuntu is the issue?

That is 1 alternative.
It could also mean that Windows doesn't validate al the same return values that Linux does, which is very common.
There are lots of times when Windows can do things because it ignores failures that Linux doesn't.  If you like, you can call that a driver issue ... but which part of the chain has it?
If it works in Windows, that is a good data point, but it doesn't completely remove other problems.  It also means that nvidia doesn't test with your monitor and Linux, which isn't surprising.  It isn't like they will correct anything and nobody except nvidia can possibly correct stuff like that.

Now, if you get Windows to dump the edid from the monitor and that information contains the equivalent of a "modeline", then you could put that into your xorg.conf and probably use it.  My GT 1030 had a mode where I was able to force a binary EDID file and override the lacking information that didn't get sent through to the GPU.  I ran with this method for about 4 yrs.
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
...
    **Option "CustomEDID" "DFP-0:/etc/X11/xorg-monitor.dell-2412m.edid.raw"    **
EndSection
```

I was trying to avoid that, since I don't know how to get the raw edid information except using Linux tools to be used in that CustomEDID line. Of course, feel free to figure it out and do something similar.

---

### Post by mark bower on 2023-01-28
o.k.  I'll pursue, maybe a bit slower in responding.  Sounds like a plan definitely worth trying, but if I can capture the parameters I will need a bit of help how to enter into the xorg.conf file.  So either way (success or not) I will return with a response.

BTW - I did contact Nvidia customer service and response was worthless; the equivalent of no response.

---

### Post by TheFu on 2023-01-29
> **mark bower said:**
>  BTW - I did contact Nvidia customer service and response was worthless; the equivalent of no response.

You are in good company.  Google for an image: "linus nvidia finger"  Screw it: [https://www.wired.com/2012/06/torvalds-nvidia-linux/](https://www.wired.com/2012/06/torvalds-nvidia-linux/)

---

### Post by mark bower on 2023-01-30
Scope:  1) long story short, Nvidia pursuit hopeless, 2) my experience getting to 2560 x 1600 via Nvidia Control Panel, 3) a fantastic post that might work for my situation, but need your guidance/input.  The following discussion is per Ubuntu, not Win10.

2) In Nvidia Control Panel I could change the resolution to 2560 x 1600 (scaled).  And it does the trick for my ACAD2000 display under WINE.  In so doing, etc/X11/xorg.conf went from 93 bytes to 20.6kb.  The change is reflected in the following text:

93 Bytes (orig xorg.conf)
```
Section “Device”
   Identifier “Intel”  (looking at Intel CPU with iGPU versus the GTX1060 GPU, Nvidia?)
   Driver “Intel”
   #Option “AccelMethod” “uxa”
End Section
```

20.6kb (expanded xorg.conf)
[omitted sections]
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       15.0 - 81.0
    VertRefresh     24.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NVIDIA GeForce GTX 1060 6GB"
EndSection

Section "Screen"
# Removed Option "metamodes" "nvidia-auto-select +0+0 {viewportin=2560x1600, viewportout=3456x2160+192+0}"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "3840x2160 +0+0; nvidia-auto-select +0+0 {viewportin=2560x1600, viewportout=3456x2160+192+0}"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

All would be good, except that the resolution becomes “locked” to the 2560 x 1600 display.  System Settings>Displays does not allow switching between the max res and 2560 x 1600 display; I reset the system back to 3840 x 2160.

3)  Please look at the link titled Modeline Calculator.  I came across it by pure luck.  A very comprehensive and informative piece on modelines!  This may be the answer to the display issue my PC has.  

[https://arachnoid.com/modelines/](https://arachnoid.com/modelines/)

When I run the program in Modeline Calculator, I get the following modeline for the resolution I am after:

# 2560x1600 @ 60.00 Hz (GTF) hsync: 99.36 kHz; pclk: 348.16 MHz
Modeline "2560x1600_60.00" 348.16 2560 2752 3032 3504 1600 1601 1604 1656 -HSync +Vsync

The question is how to correctly marry this info into the xorg.conf file, into the Monitor Section?  By making the resolution change and then backing out, well, that seems to give the “HorizSync” and “VertRefresh” ranges as seen in the two Monitor Sections.  I can return and add in the xorg.conf Sections I omitted if helpful.

What do you think?

---

### Post by TheFu on 2023-01-30
> **mark bower said:**
>  
What do you think?

I've never used a modeline that wasn't generated by monitor EDID information.  In the 1990s, people could destroy their monitor using the wrong modeline information, so I cannot suggest you use the line unless you get it from the monitor manufacturer or from EDID generated directly by the monitor connection.  I will not be responsible or encourage you to destroy your TV.

Post #9 has modelines you can use.  You can put those into your xorg.conf.d/ directory within the section shown. 1 or 50 or more modelines are allowed.

---

### Post by mark bower on 2023-01-30
Well, looks like this may be the end of the line.  Both the EDID dump info from the Monitor-TV and your post #9 do not address the resolution I need.  If I go to Samsung, they are not likely to address the missing resolutions in Ubuntu, vs the same resolutions which are provided in Windows. I will return to this thread (I heed your advice) if I ever come up with anything.  Else, I will have to work with what I have.

Thanks for hanging in and trying to help.
mark

---

### Post by TheFu on 2023-01-31
Does MS-Windows not have a tool to dump EDID information from a monitor?

---

### Post by mark bower on 2023-01-31
In post #15 I skipped talking re Windows as "Scope: 1) long story short, Nvidia pursuit hopeless," - I should have said Windows-Nvidia pursuit.  I could not get to the Windows Nvidia EDID dump because the Nvidia Control Ctr on my computer would not give the "Workstation>View System Topology" option(this is the path from a post I read). Other options like "3D Setings,Display,Video,etc" were available.  But no matter, the output is stated to be in hexadecimal.

Now, if you have Windows available, please the link:
```
https://nvidia.custhelp.com/app/answers/detail/a_id/3571/~/managing-a-display-edid-on-linux
```
It has "nvidia-settings" open a GUI which provides for EDID output in either binary or hex. It suggests how to modify the xorg.conf file, but I cannot follow.  There is no convenient Modeline provided.  In following the steps, for the Samsung EDID I got one long string of hex numbers in the output file.

---

### Post by TheFu on 2023-01-31
In post #12, I showed how to use a custom EDID (i.e. the binary EDID file).

---

### Post by mark bower on 2023-02-04
I have been remiss in not responding to your replies.  I guess based on my experience level, I had difficulty in following your guidance.  BUT, I really appreciate as always your effort and time to try and help me.  

The method described below was provided to me and it works. A different screen resolution can be substituted for 2560 x 1600, which is the resolution I needed.

1) If Nouveau is not the driver, then install Nouveau as the driver.

2) Use the “cvt” command to determine modeline parameters for a given screen resolution:

```
mark@senior:~$ cvt 2560 1600 60
# 2560x1600 59.99 Hz (CVT 4.10MA) hsync: 99.46 kHz; pclk: 348.50 MHz
Modeline "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
```

3) Copy the below into a terminal and execute.  The .xprofile is stored at /home/mark for my PC.

```
cat<<SCREENFIX >"$HOME/.xprofile"
#!/bin/sh
xrandr --newmode "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
xrandr --addmode HDMI-0 "2560x1600_60.00"
SCREENFIX
```
It’s that simple.  And now in Settings>Display I can select the 2560 x 1600 when needed, and then change back to the native resolution.

---

### Post by TheFu on 2023-02-05
I completely forgot about 'cvt'. Sorry.

---

