---
title: "Changing Default screen resolution"
date: 2016-10-19
forum: Hardware
---

### Post by col48 on 2016-10-19
Just installed 16.04 on a machine which runs 12.04 happily.

The default screen resolution is 1680 x 1050, when I need it to be 1600 x 1000 - I am assuming this is why I need to reset it each time after login.
How do I change the default?

Here is the output of xrandr (NB I have changed to 1600x1000 via System Settings already in this session):```

Screen 0: minimum 320 x 200, current 1600 x 1000, maximum 4096 x 4096
VGA-0 connected primary 1600x1000+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050     59.88 +
   1600x1200     60.00  
   1600x1000     60.01* 
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1152x864      75.00  
   1152x720      59.97  
   1024x768      75.08    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   640x480       75.00    66.67    60.00  
   720x400       70.08  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
```

My video card is Nvidia. [Edit: no it isn't - see later post]

All the nearly relevant threads or help elsewhere seem to start from the position of the desired resolution not being on offer, which is not my position.

---

### Post by col48 on 2016-10-19
I still haven't found a solution except for running xrandr in a shell script on startup - which doesn't change the default, merely overrides it.

But the following link

[http://unix.stackexchange.com/questions/266085/is-the-current-screen-resolution-saved-to-a-file-anywhere]("http://unix.stackexchange.com/questions/266085/is-the-current-screen-resolution-saved-to-a-file-anywhere")
does suggest a possible solution by writing to /sys/class/graphics/fb0/mode, which - if it works - sounds like a permanent solution if these files are not overwritten on bootup.

The article claims that the mode file contains the current resolution and the modes file contains the possible resolutions.
But on my machine, both files are 4.1kb: the mode file seems to be empty or all blank and the modes file contains a single line, something like U1600x1050-0

There is also an fb0con/subsystem/fb0 folder which as far as I can see mirrors the fb0 folder.

Any thoughts?

[Thanks @deadflowr for sorting tags for the link - I've never put a link in a post before]

---

### Post by col48 on 2016-10-21
Now I think the fb0 path is a red herring.

Looks like running ```
xrandr -s 1600x1000
``` at startup is the best workaround

---

### Post by Yellow Pasque on 2016-10-22
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)

So if you're using the proprietary nvidia driver, it probably created an /etc/X11/xorg.conf for you. Post it and maybe it's just a matter of adding a line like this to the monitor section:
```
Option          "PreferredMode" "1600x1000_60.00"
```

---

### Post by col48 on 2016-10-22
Thanks, Temujin.  I've read the article, but...

I can't remember whether I am using the proprietary driver (it would be 8 years ago now, and someone else did the work), but there is no xorg.conf that I can find in the file system.
But even if there is, shouldn't the manual System Tools action overwrite it?

This is what is in /etc/X11:
[ATTACH=CONFIG]271732[/ATTACH]

No .conf of any kind.

Still baffled & frustrated by the panel questions.

---

### Post by Yellow Pasque on 2016-10-23
> I can't remember whether I am using the proprietary driver
Check:
```
glxinfo | grep string
```
Or check which kernel module is in use (nvidia=proprietary, nouveau=opensource):
```
lspci -k
```

> but there is no xorg.conf that I can find in the file system.
It doesn't exist by default in modern Linux distros, but you can create one.

> But even if there is, shouldn't the manual System Tools action overwrite it?
I would think, but I use xfce desktop, so I'm not the one to ask.

> Still baffled & frustrated by the panel questions
Then just continue to run the xrandr command at startup. Unless you have a system with many users or absolutely insist on the login screen being the preferred resolution, is it really a major issue?

---

### Post by col48 on 2016-10-23
glxinfo output:
```
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: Mesa Project
OpenGL renderer string: Mesa DRI R200 (RV280 5960)  DRI2
OpenGL version string: 1.3 Mesa 11.2.0

```
lspci output (what look like relevant parts only):
```
00:01.1 SMBus: NVIDIA Corporation MCP65 SMBus (rev a1)
	Subsystem: Micro-Star International Co., Ltd. [MSI] MCP65 SMBus
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c_nforce2

00:09.0 IDE interface: NVIDIA Corporation MCP65 IDE (rev a1)
	Subsystem: Micro-Star International Co., Ltd. [MSI] MCP65 IDE
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd, pata_acpi
00:0a.0 IDE interface: NVIDIA Corporation MCP65 SATA Controller (rev a3)
	Subsystem: Micro-Star International Co., Ltd. [MSI] MCP65 SATA Controller
	Kernel driver in use: ahci
	Kernel modules: ahci, pata_acpi
00:0b.0 PCI bridge: NVIDIA Corporation MCP65 PCI Express bridge (rev a1)
	Kernel driver in use: pcieport
	Kernel modules: shpchp

01:08.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 PRO] (rev 01)
	Subsystem: Connect Components Ltd RV280 [Radeon 9200 PRO]
	Kernel driver in use: radeon
	Kernel modules: radeonfb, radeon

```

And no, it's not a major issue, but annoying just the same.  And understanding what is under the lid may be useful in the future.

---

### Post by Yellow Pasque on 2016-10-23
> **col48 said:**
> My video card is Nvidia.

No, it's not. The motherboard has an nvidia chipset, but the graphics card is an ATI:
```
01:08.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 PRO] (rev 01)
	Subsystem: Connect Components Ltd RV280 [Radeon 9200 PRO]
	Kernel driver in use: radeon
```


Anyway, this is what I was getting at when I linked to the X config wiki page (basic xorg.conf skeleton with preferredmode line):
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Option          "PreferredMode" "1600x1000_60.00"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by col48 on 2016-10-23
Thanks for correcting my misunderstanding, Temüjin.

It will be a few days before I can get to this again, but I will set up an xorg.conf file with the contents you suggest and see what happens.

Thanks for your help with this - it's a bit out of my comfort zone, as you can tell!

---

### Post by col48 on 2016-10-29
Unfortunately, this made no difference.

I created /etc/X11/xorg.conf owned by root with permissions -rw-r--r-- pasted in the text in post 8, added the comments at the top and it made no difference.
I then added the Driver line and nor did that.

What next?

xorg.conf reads thus at present:
```

# hand crafted by copy+paste 2016-10-29
# from https://ubuntuforums.org/showthread.php?t=2340517 post #8
# Driver added

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Option          "PreferredMode" "1600x1000_60.00"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by col48 on 2016-11-15
This has moved on slightly.

It appears that *something* is setting the screen resolution back to the 'natural' size after all my efforts to set it otherwise on login.

This is not a show-stopper, but an irritation, the resolution of which should be educational - for me, at least!

1. My xorg.conf remains as in the previous post.

2. My ~/.profile now looks like this (the xxxx substitutes for the full path):```

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

# added by hand 2016-11-15
/home/xxxx/screenres.sh
```

The script file (screenres.sh) looks like this - NB no #!/bin/bash line:
```
echo "screenres BEGIN" >> ~/z.txt
date >> ~/z.txt
echo "before xrandr" >> ~/z.txt
xrandr >> ~/z.txt
xrandr -s 1600x1000
echo "after xrandr" >> ~/z.txt
xrandr >> ~/z.txt
date >> ~/z.txt
echo "screenres END" >> ~/z.txt

```

and after a single reboot, /z.txt looks like this:
```
screenres BEGIN
Tue 15 Nov 14:41:22 GMT 2016
before xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA-0 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050     59.88*+
   1600x1200     60.00  
   1600x1000     60.01  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1152x864      75.00  
   1152x720      59.97  
   1024x768      75.08    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   640x480       75.00    66.67    60.00  
   720x400       70.08  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
after xrandr
Screen 0: minimum 320 x 200, current 1600 x 1000, maximum 4096 x 4096
VGA-0 connected primary 1600x1000+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050     59.88 +
   1600x1200     60.00  
   1600x1000     60.01* 
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1152x864      75.00  
   1152x720      59.97  
   1024x768      75.08    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   640x480       75.00    66.67    60.00  
   720x400       70.08  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
Tue 15 Nov 14:41:23 GMT 2016
screenres END

```

The content of z.txt proves that the script ran and that xrandr did something.
But when the desktop shows up, it is back at 1680x1050.

So what can be changing it back?

*If I run the shell manually it duly changes the display (or not if already as desired) as expected and writes to z.txt.*

---

### Post by col48 on 2016-12-01
No further progress on this.

So what is going on?

PS: where does the list of possible screen res come from?  The file which can be seen in a running system appears to be written at boot time.  I was wondering if I could force it to default differently.

---

### Post by col48 on 2016-12-10
bump...

NOT solved.

---

### Post by Yellow Pasque on 2016-12-10
I'd suspect Unity desktop is doing something to change the resolution. You may want to try another desktop to see if it happens there.

> PS: where does the list of possible screen res come from?
Usually read from the monitor's EDID.

---

### Post by col48 on 2016-12-11
Thanks Temujin.
I have tweaked Unity, am using the Classic Gnome desktop (as I did with 12.04 with no issue)

The output from parse-edid is this:
```
Section "Monitor"
	Identifier "PLE2003WSV"
	ModelName "PLE2003WSV"
	VendorName "IVM"
	# Monitor Manufactured week 19 of 2008
	# EDID version 1.3
	# Analog Display
	DisplaySize 430 270
	Gamma 2.20
	Option "DPMS" "true"
	Horizsync 31-83
	VertRefresh 55-76
	# Maximum pixel clock is 170MHz
	#Not giving standard mode: 1152x720, 60Hz
	#Not giving standard mode: 1280x960, 60Hz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1600x1000, 60Hz
	#Not giving standard mode: 1600x1200, 60Hz
	#Not giving standard mode: 1680x1050, 60Hz
	Modeline 	"Mode 0" 119.00 1680 1728 1760 1840 1050 1053 1059 1080 +hsync -vsync 
EndSection

```

Could the lack of 1600 and 1000 in the Modeline have something to do with the reluctance to use 1600x1000 unless I force it manually?
Is this a useful avenue to explore?

I prefer not to try another desktop - at least I have a workaround for this one, and I am used to it.....

---

### Post by davethescientist on 2017-02-02
I've been dealing with this myself col48, and I appreciate that you've documented your progress. It's helped me quite a lot. Have you seen [this page]("https://wiki.ubuntu.com/X/Config/Resolution") on methods to set the resolution? It says that the .xprofile (and I assume .profile) are run relatively late in the process, which is why the login screen isn't affected. It also details alternatives, such as setting up a xorg.conf (a more detailed example than the one you were previously given), as well as adding the xrandr command to the kdm/gdm startup scripts.

---

### Post by col48 on 2017-02-03
Thanks Dave

Yes, I read the page you cite, and the earlier posts document what I did as a result.  I do not know where the kdm/gdm script(s) might be.  Neither /etc/gdm nor /etc/kde4 are present on my machine, so I have not followed up that one.  And surely anything launched in the startup applications list must execute after anything more boot/system side?  Whatever is pushing the undesired resolution is doing it after that.

As I said before, this is outside my comfort zone - I only have a hazy idea of how these things mesh together, and I know that a little knowledge can lead to disaster!

---

