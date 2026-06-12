---
title: "dispaly problem  with ubuntu 8.04"
date: 2008-07-25
forum: Hardware
---

### Post by miguelbuenca on 2008-07-25
I just installed ubuntu (hardy Heron) to my laptop, fUJITSU SIEMENS AMILO PRO V2010. Processor celeron 1.5 m, ram 512 mb sdram, display properties VIA/S3G UNICHROME PRO IGP. My problem I can't unjust the display resolution. It stuck to 640x480 which make it big for my laptop monitor. Don't know what to do. I'm not really good in computers so please help. Thanks

---

### Post by miguelbuenca on 2008-07-26
Anybody out there help please

---

### Post by northern lights on 2008-07-26
Can you please post the output of ```
sudo lshw -C display
```

Thank you.

---

### Post by miguelbuenca on 2008-07-26
thanks for your reply. Sorry, am not quite technical in computers. Can you detail the proceedure how I can get the information you want. Thanks

---

### Post by northern lights on 2008-07-26
Open a terminal ("Applications" menu or "Alt+F2" & "gnome-terminal") and paste the code from my previous post in the terminal window. Hit enter. Mark the newly appeared text (below the "user@host:~$sudo lshw..."), copy it ("Edit" context menu or "Ctrl+Alt+C) and paste it in a new post here.

---

### Post by miguelbuenca on 2008-07-26
[sudo] password for miguel: 
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by miguelbuenca on 2008-07-26
THANKS NORTHERN LIGHTS FOR BEARING WITH ME. i HOPE i SENT YOU THE RIGHT INFO YOU WANTED

---

### Post by northern lights on 2008-07-26
You must have issued wrong options, as that output is simply the '--help' output.

Please run what I posted verbatim. 'sudo lshw -C display'...

---

### Post by miguelbuenca on 2008-07-26
miguel@miguel-laptop:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: S3 Unichrome Pro VGA Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2
miguel@miguel-laptop:~$

---

### Post by northern lights on 2008-07-26
mkey. For whatever reason Ubuntu did not automatically configure drivers for your graphics card.

Good news is, drivers exist. You might want to to check [www.openchrome.org]("www.openchrome.org")for references. However, there should be no need to download the driver from the site, as it should be included in the Hardy repos.

Can you run ```
aptitude search chrome
```and check whether the packages 'xserver-xorg-video-unichrome', 'xserver-xorg-video-openchrome', 'libchromexvmc1' and 'libchromexvmcpro1' are installed?
--> Check whether there's an "i" flag left of the respective packages.

If not, install them with ```
sudo apt-get install PACKAGENAME
```

If you're more comfortable with Synaptic, check & install those 4 packages from there.

Fixed? If not: reboot.

Fixed? If not: Run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by miguelbuenca on 2008-07-26
Thanks mate for your time. I appreciate your help. I think I can follow your instructions. I learning in the process. thanks

---

### Post by miguelbuenca on 2008-07-26
this is what i got. don't know what it means 

miguel@miguel-laptop:~$ aptitude search chrome
i   libchromexvmc1                 - XvMC Libraries used by the Openchrome V
i   libchromexvmcpro1              - XvMC Pro Libraries used by the Openchro
p   xfce4-theme-brushedchrome      - BrushedChrome theme for Xfwm4 and Gtk+ 
i   xserver-xorg-video-openchrome  - X.Org X server -- VIA display driver   
p   xserver-xorg-video-unichrome   - X.Org X server -- VIA display driver   
miguel@miguel-laptop:~$ sudo apt-get install PACKAGENAME
[sudo] password for miguel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package PACKAGENAME
miguel@miguel-laptop:~$ sudo apt-get install xserver-xorg-video-unichrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-video-unichrome: Depends: xserver-xorg-core (>= 1:1.1.1) but it is not going to be installed
E: Broken packages
miguel@miguel-laptop:~$ sudo apt-get install xserver-xorg-video-unichrome xserver-xorg-video-openchrome', 'libchromexvmc1' and 'libchromexvmcpro1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-video-openchrome, libchromexvmc1 and libchromexvmcpro1
miguel@miguel-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080726202923
miguel@miguel-laptop:~$

---

### Post by northern lights on 2008-07-26
Okay. I'm sorry - I should have gone in slower steps.
```
miguel@miguel-laptop:~$ aptitude search chrome
i [COLOR="Blue"]libchromexvmc1[/COLOR] - XvMC Libraries used by the Openchrome V
i [COLOR="Blue"]libchromexvmcpro1[/COLOR] - XvMC Pro Libraries used by the Openchro
p [COLOR="Red"]xfce4-theme-brushedchrome[/COLOR] - BrushedChrome theme for Xfwm4 and Gtk+
i [COLOR="Blue"]xserver-xorg-video-openchrome[/COLOR] - X.Org X server -- VIA display driver
p [COLOR="SeaGreen"]xserver-xorg-video-unichrome[/COLOR] - X.Org X server -- VIA display driver 
```
Each colored text represents a "package".
Notice the 'i' ^ 'p' flags to the left.
The blue packages are installed. The red one is of no interest to us.

Let's install the green one.

Run ```
sudo apt-get install xserver-xorg-video-unichrome
```

Any changes?

Probably not. Reboot.

Any changes?

Run ```
sudo lshw -C display
```again. Does it still read 'UNCLAIMED'? Report back, we'll take it from there.


[EDIT]
You see, "PACKAGENAME" was a placeholder and meant to be replaced by the name(s) of the uninstalled package(s)...
[/EDIT]

---

### Post by miguelbuenca on 2008-07-26
This is what I got. Will reboot after i send this message

miguel@miguel-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080726202923
miguel@miguel-laptop:~$ sudo apt-get install xserver-xorg-video-unichrome
[sudo] password for miguel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-video-unichrome: Depends: xserver-xorg-core (>= 1:1.1.1) but it is not going to be installed
E: Broken packages
miguel@miguel-laptop:~$

---

### Post by miguelbuenca on 2008-07-26
Hurray!!! Bingo. The display is much better at 800x700 Thanks. Though it does not fit all on the monitor its definiely much better. Heres a copy of the report...

miguel@miguel-laptop:~$ sudo lshw -C display
[sudo] password for miguel: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: S3 Unichrome Pro VGA Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2
miguel@miguel-laptop:~$

---

### Post by northern lights on 2008-07-26
It can't be better. That's a fluke.

Thought you could install openchrome and unichrome parallel. Can't.

Reconfiguring X might have changed something, but it's gotta be way better than 800x700 (what weird resolution is that anyway?).

Can you post your xorg.conf?

```
gedit /etx/X11/xorg.conf
```

---

### Post by miguelbuenca on 2008-07-26
Sorry resolution is 800X600. Anyway, Am happy. You've done a great job for me tonite mate. Thanks. I wish I could treat you for a beer. hehehe. Thanks again.
Mike

---

### Post by northern lights on 2008-07-26
Okay, fair enough. If you don't want more than 800x600 anyway, all the better.

And that you learned a few basic things at the side, also perfect.

Yet let me explain that we didn't even install any new packages, since unichrome and openchrome drivers apparently can't be installed simultaneously.

When you ran ```
sudo dpkg-reconfigure -phigh xserver-xorg
```you ran an automatic reconfiguration of your [X]("http://en.wikipedia.org/wiki/X_Window_System"). That resulted in 800x600 being available.

Your still in VESA mode and your graphics chip is still not running under a specific driver however.

1024x780 should minimally possible with that chip...

---

### Post by mikejaegerster on 2008-07-26
Northern,

I am having a similar problem with an old nVidia GeForce2 MX200.  I can only get to 800x600:

mike@mike-desktop:~$ sudo lshw -C display
[sudo] password for mike: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV11DDR [GeForce2 MX200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: b2
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5
mike@mike-desktop:~$ aptitude search chrome
i   libchromexvmc1                  - XvMC Libraries used by the Openchrome VIA 
i   libchromexvmcpro1               - XvMC Pro Libraries used by the Openchrome 
p   xfce4-theme-brushedchrome       - BrushedChrome theme for Xfwm4 and Gtk+ 2.0
i   xserver-xorg-video-openchrome   - X.Org X server -- VIA display driver      
p   xserver-xorg-video-unichrome    - X.Org X server -- VIA display driver      

Here is contents of xorg.conf:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by miguelbuenca on 2008-07-26
> **northern lights said:**
> It can't be better. That's a fluke.

Thought you could install openchrome and unichrome parallel. Can't.

Reconfiguring X might have changed something, but it's gotta be way better than 800x700 (what weird resolution is that anyway?).

Can you post your xorg.conf?

```
gedit /etx/X11/xorg.conf
```

Sorry mate, I missed what you wanted me to post. I tried typing the command. It just opened up a blank window. Surely I wanted to get a better resolution if you have more time to spare. Or maybe next time. Thanks

---

### Post by northern lights on 2008-07-26
@miguel:
Most probably you neglected the capital X in X11 - 'gedit /etc/**X**11/xorg.conf'.

@mike:
Sure you're problem is similar when it comes to how you're screen looks and to the fact, that you don't have proper drivers setup either. Yet while his card is that horrid S3 Unichrome Pro, you're GeForce2 should be of no problems.

First log out of you're current X session (watch out - you'll have to cope with commandline only, so jot down the next few lines)```
sudo /etc/init.d/gdm stop
```

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the interface with ```
sudo /etc/init.d/gdm start
```

Try to increase resolution.

If it fails, run ```
sudo apt-get install nvidia-glx nvidia-settings
```('nvidia-glx' is the generic X.org nvidia driver and 'nvidia-settings' adds "System > Administration > nVidia X Server Settings)" and append this section ```
Section "Device"
	Identifier	"Configured Video Device"
	[COLOR="RoyalBlue"]Driver		"nvidia"[/COLOR]
EndSection
```of your xorg.conf by the text in blue.

Reboot or Restart the session (Ctrl+Alt+Backspace or '/etc/init.d/gdm start/stop).

---

### Post by miguelbuenca on 2008-07-26
Sorry, now I got it right. heres the report....
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by northern lights on 2008-07-26
> **miguelbuenca said:**
> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Change the above section to:

```
Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
EndSection
```

and reboot / restart X session.

Now what?

---

### Post by miguelbuenca on 2008-07-26
> **northern lights said:**
> Change the above section to:

```
Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
EndSection
```

and reboot / restart X session.

Now what?

I edited the line  as you instructed and tried to save changes but got message 
"I don not have permission necessary to save the file.Please checked that you typed the location correctly and try again". Do I need to save? or just reboot?

Here's a copy of changes I made:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"   
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by miguelbuenca on 2008-07-26
I tried to reboot anyway but was prompted by the application to save. Again I everytime I get thesame message. Anyway, I know we're on a different time zone. You must be resting now.I'm in Saudi Arabia. I'll wait till you go online next again. I have to pack up to go to work. Thanks again friend.
Miguel

---

### Post by idsi on 2008-07-27
I have a similar problem. Could this have something to do with BIOS options?

Should I set my BIOS for Plug&Play OS.

Is that why the drive is not "claiming" the device?

---

### Post by northern lights on 2008-07-27
> **miguelbuenca said:**
> "I don not have permission necessary to save the file.Please checked that you typed the location correctly and try again". Do I need to save? or just reboot?
You do need to save it.

For you to have permission to alter a system file, you have to open it as root.

Run ```
gksu gedit /etc/X11/xorg.conf
```in order to be able to save.

---

### Post by miguelbuenca on 2008-07-27
> **northern lights said:**
> You do need to save it.

For you to have permission to alter a system file, you have to open it as root.

Run ```
gksu gedit /etc/X11/xorg.conf
```in order to be able to save.

I type in this code and made changes as you instructed after saving I rebooted. Something went wrong cause my dispaly now went back to 640x480.

I'm sending here copy of the report. 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Boardname	"via"
	Busid		"PCI:1:0:0"
	Driver		"via"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by mikejaegerster on 2008-07-27
northern,

Update - 9:24 PM EDT

You were right, I was chasing multiple problems.  The first was to get the driver running.  The second was for the system to recognize my PnP ViewSonic VA712b monitor.  Once I installed the driver from the nVidia website, and got the nvidia-settings and nvidia-xconfig running, the system was able to better detect my hardware.  I want to thank you for all the little tidbits I learned from you while I was reading this thread.  You were a big help.

Mike

---

### Post by northern lights on 2008-07-28
You're welcome.

See this is the beauty of Linux - it's not just the awesomest OS, it also comes with a community.

---

### Post by miguelbuenca on 2008-07-28
I'm glad to see you back on this thread northern light mate. Sorry to bugger you, but I'm now stuck again to 640x480 resolution. I'm not sure now if there's still hope to make this resolution better. Am thinking now to uninstall ubuntu and start from the begining again. Even that is still a problem cause I don't know how to uninstall it. I hope you can give me some advise. Thank you.
Miguel

---

### Post by northern lights on 2008-07-28
As for a quick 800x600, do what you did last time (autoreconfigure X).

An option to "uninstall" comes with no OS whatsoever. Simply put a new one ontop of it / format the partition.

Please don't turn your back on Ubuntu just because of this graphics issue, though.

Of hand I don't know what to say about the S3 Unichrome, so lemme inform myself and get back to you. I'd rather shut up than give misinformation.

---

### Post by miguelbuenca on 2008-07-28
Yes I got it back to 800x600. Am happy Thanks. I think thats the most I can for now. Its actually a good learning expirience messing with this resolution issue. I'll just check this forum for any update for my dispaly card. Thanks again mate. You're a great help.  
Miguel

---

