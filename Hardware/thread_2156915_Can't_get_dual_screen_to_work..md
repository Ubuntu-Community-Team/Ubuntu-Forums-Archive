---
title: "Can't get dual screen to work."
date: 2013-06-23
forum: Hardware
---

### Post by Alaza on 2013-06-23
Hi guys.

I've always had difficulty getting dual screen up and running on my desktop running Ubuntu.

Today I installed a 12.04 LTS XUbuntu on my desktop with a Radeon HD 7850, and when it booted I only had one screen enabled. My setup is as follows:

Primary: 720p monitor with DVI connection.
Secondary: 1080p monitor with DVI to VGA converter (the monitor only has VGA output - no clue why).

I've installed the newest driver from:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

And when I run xarndr -q I get:

```
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1680 x 1680DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 disconnected (normal left inverted right x axis y axis)
DFP6 connected 1400x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0 +
   1400x1050      60.0* 
   1280x1024      60.0     75.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DFP7 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1400x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0 +
   1400x1050      60.0* 
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        59.9  
```

I've tried commands like:

```
 xrandr --output DFP6 --mode 1024x768 --output CRT1 --mode 1024x768 --right-of DFP6  
```

And I get this: "xrandr: screen cannot be larger than 1680x1680 (desired size 2048x768)"

What am I doing wrong?

---

### Post by jp734 on 2013-06-23
xrandr detected the two monitor but for some reason the system thinks there is only one. Hows your xorg.conf?

I was able to get my triple monitor working but just cant get the background to span on all three.

---

### Post by Alaza on 2013-06-23
Based on this topic: [https://www.linuxquestions.org/questions/linux-general-1/xrandr-screen-cannot-be-larger-than-595649/](https://www.linuxquestions.org/questions/linux-general-1/xrandr-screen-cannot-be-larger-than-595649/) I tried to include "modes" and virtual in my /etc/X11/xorg.conf.fglrx-1, however after re-logging I never got anything but black screens. Now I've reloaded the original xonf and I've got a "AMD Unsupported Hardware" logo in the right hand corner.

```
Section "ServerLayout"	Identifier     "aticonfig Layout"
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
	BusID       "PCI:1:0:0"
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

I've c/p'ed my conf as it is at the moment.

Thanks.

---

### Post by jp734 on 2013-06-24
Okay, a few things that we need to do:

 - We need to add Xinerama on your configuration.
   Section "ServerFlags"
            Option   "Xinerama" "on"
   EndSection

 - Next, add this to your 'SubSection "Display" '
            Virtual  2048 2048

 - Finally, I just want to make sure, because sometimes it's the simplest thing that we forget to do. After editing your  /etc/X11/xorg.conf.fglrx-1, did you rename it as "xorg.conf"?

Hopefully, this works. If not, let us know. BTW, are you using one video card only?

---

### Post by Alaza on 2013-06-24
Are you sure about the 2048 2048 part? Seeing I have a 1080p and a 720p monitor which optimally should be running 1920x1080 and 1680x1050?

I did not rename my .xorg.conf. Should I have?

Yes, I am running with one video card only.

---

### Post by jp734 on 2013-06-24
Well, basing on your xrandr command *"xrandr --output DFP6 --mode 1024x768 --output CRT1 --mode 1024x768 --right-of DFP6"*, yes *"virtual 2048 2048"* should be fine. And yes, you should rename the file to xorg.conf. That is the file the system will look for. The other one is a backup created AMD when you tried to reconfigure your setup (AMD Catalyst Control Center perhaps).

You can always change the virtual setting to a higher res later on. For now, at least try that if it works.

---

### Post by Alaza on 2013-06-24
Actually I do have a version of the Catalyst Control Center installed, however I seem to be unable to use it. I get a segment fault (core dumped) when I run it.

Do you know how I verify which version I have of it?

I'll definitely try your suggestion tonight when I get off from work. Thank you very much. :)

---

### Post by Alaza on 2013-06-25
```
Hi again.

So I tried to change the settings to the ones you suggested. At the moment my xorg.conf in X11 is looking like this:

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection


Section "Module"
EndSection


Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection


Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Virtual 2048 2048
    EndSubSection
EndSection

Section "ServerFlags"
    Option "Xinerama" on
Endsection
```

If I've got the ServerFlags section on I just get two black screens at login. If I remove it while keeping the Virtual 2048 2048 I get in with who monitors that are identical and a xrandr -q that looks like this:

```
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 2048 x 2048DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 disconnected (normal left inverted right x axis y axis)
DFP6 connected 1400x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0 +
   1400x1050      60.0* 
   1280x1024      60.0     75.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DFP7 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1400x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0 +
   1400x1050      60.0* 
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        59.9  



```

Any suggestions?

---

### Post by jp734 on 2013-06-25
What kernel are you using?
Terminal>uname -v

Did you use the driver from Ubuntu?

Look at /var/log/Xorg.0.log for some clue

The reason I'm asking is because I had some trouble with kernel 3.8.0.25 but works just fine with 3.8.0.23.  Also I used the driver I've downloaded from AMD. Now that will be up to you if you want to go that route . Lets first check your kernel version and for some clues.

---

### Post by jp734 on 2013-06-25
By the way, you get the unsupported hardware logo because the driver is outdated for your card. That's the reason why I downloaded the driver from AMD.

---

### Post by Alaza on 2013-06-25
Okay, so I got to a point where I tried to --force reintall my AMD drivers for my graphic card and eventually ended up with a dead XUbuntu.

So I just made a complete reinstall of the 64-bit desktop version, and only installed security updates. At this point I only have my primary monitor enabled by default.

From jockey-text -l I get this:

```
kmod:fglrx_experimental_12 - Experimental AMD binary Xorg driver and kernel module (Proprietær, Deaktiveret, Ikke i brug)
xorg:fglrx - ATI/AMD proprietær FGLRX-grafikdriver (Proprietær, Deaktiveret, Ikke i brug)
xorg:fglrx_experimental_9 - ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) (Proprietær, Deaktiveret, Ikke i brug)
xorg:fglrx_updates - ATI/AMD propritær FGLRX grafikdriver (opdateringer efter udgivelse) (Proprietær, Deaktiveret, Ikke i brug)

```

The weird thing is that "Ikke i brug" means "Not used". So which driver is actually running?

In my /etc/X11/ I've only got this:


```
app-defaults
cursors
default-display-manager
fonts
rgb.txt
X
xinit
xkb
Xreset
Xreset.d
Xresources
Xsession
Xsession.d
Xsession.options
Xwrapper.config
```

So no xorg.conf or anything like that with the default drivers?

From /var/log/Xorg.0.log I got this (amongst a whole many other things):

```
Current Operating System: Linux ubuntu 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 x86_64
```

Edit:

I might try this in the end? I just checked my xrandr, and with the native Ubuntu driver xrandr does only see one monitor at all:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 400, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050       0.0* 
   1280x1024       0.0  
   1280x960        0.0  
   1152x864        0.0  
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
   720x400         0.0
```

---

### Post by jp734 on 2013-06-25
Ok, so we are starting FRESH!

To find out what driver is being used, on terminal type "lspci -k". This should list all your pci devices and the drivers being used.

If fglrx is not being used, you have to make a decision. Are you going to use the driver from Ubuntu or from AMD website. With Ubuntu, more likely you will again get the "Unsupported Hardware" logo at the bottom right of your screen. It doesn't mean it will not work (not proven yet, at least from what I know). Like I said, I think it is just old enough for your NEWER video card. But you have to use fglrx as you will need Xinerama or else you will ONLY get a cloned screen.

If you decide to download from AMD site, you will need to make it an executable file and install as root:
 - sudo chmod +x "downloaded_filename"
 - sudo ./downloaded_filename

Once finished, it will instruct you to configure by entering "aticonfig --initial" and will create an xorg.conf file for you. Then you might have to manually edit the file and add the virtual 2048 2048 again.

---

### Post by jp734 on 2013-06-25
Here is a copy of my xorg.conf file. Maybe it will help you. This is a setup for three monitors with 2 video cards on lubuntu 13.04 using amd-driver-installer-catalyst-13-4-x86.x86_64.run downloaded from AMD's website.

> #------------------------------------------------------------------------------
################ S E R V E R   L A Y O U T ####################################
#------------------------------------------------------------------------------

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Screen0" 0 0
	Screen			"Screen1" RightOf "Screen0"
	Screen         "Screen2" RightOf "Screen1"
EndSection
#---------------------------------------------------------------------------------
################ M O D U L E S   A N D   F L A G S ###############################
#---------------------------------------------------------------------------------
Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection
#-----------------------------------------------------------------------------------
################ M O N I T O R    S E C T I O N ####################################
#-----------------------------------------------------------------------------------
Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1281 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "1-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "75"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection
#---------------------------------------------------------------------------------
################ D E V I C E    S E C T I O N ####################################
#---------------------------------------------------------------------------------
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[4]-0"
	Driver      "fglrx"
	Option	    "Monitor-Default monitor" "1-CRT2"
	BusID       "PCI:4:0:0"
EndSection
#---------------------------------------------------------------------------------
################ S C R E E N    S E C T I O N ####################################
#---------------------------------------------------------------------------------
Section "Screen"
	Identifier "Screen0"
	Device     "aticonfig-Device[0]-0"
	Monitor		"0-CRT1
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3840 3840
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "aticonfig-Device[0]-0"
	Monitor    "0-CRT2"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "amdcccle-Device[4]-0"
	Monitor		"1-CRT2"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection


---

### Post by Alaza on 2013-06-26
```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 6819. Subsystem: PC Partner Limited Device e221
```

This is what I got from the PCI list. Does that make you any the wiser? :)

I definitely think that using the AMD official driver is the way to go. I did run with that previously as well, before I mixed something terribly up. I'll install that now and return.

Edit:

Okay, so I installed the drivers and I could now access the AMDCCC. I can make my monitors extend the desktop now, however, it is only predefined resolutions, which means that I still can't get my 1080p beyond 1600x1200 for some reason. So I tried to mess with the resolutions in the xorg.conf file, however that made AMDCCC go completely amok, so now all windows resizing and the like is really slow and I can't see my monitors in the AMDCCC anymore. Also I get a lot of rubbish in the terminal when running amdcccle like:

```
sh: 1: gnome-session: not found
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    139 (Uknown extension)
  Minor opcode: 66 (Unknown request)
  Resource id:  0x17

```

And I get system crash reports for AMDCCC as well, which I guess means that it is more or less dead.

---

### Post by jp734 on 2013-06-26
sometimes for the monitor to work on the max resolution, you have to add its refresh rates on xorg.conf file. Do a research on your monitor and add it to the file. It should be something like this:

HorizSync  35.0-80.0
VertRefresh 50.0-85.0

You might find it on Xorg.0.log file as well.

Just remember, if messing with the xorg.conf is the only reason why your system will not work properly, you can always change your xorg.conf without reinstalling the OS. Boot from live CD or flash drive and edit xorg.conf again. EASY FIX! Once you got it back to where you can extend the desktop again then try adding the refresh rates and see. Hopefully that would be the last thing you have to do. :)

---

