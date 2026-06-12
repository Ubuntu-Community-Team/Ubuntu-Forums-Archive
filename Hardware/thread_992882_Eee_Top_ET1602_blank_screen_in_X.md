---
title: "Eee Top ET1602: blank screen in X"
date: 2008-11-25
forum: Hardware
---

### Post by radu.c on 2008-11-25
Hi,

I have two new shiny Asus Eee Top ET1602 systems. I tried running Ubuntu 7.10 and 8.10 on them. In the console, and while showing the splash, the screen works fine. When X starts with the intel driver the backlight seems to go off.

I tried multiple way to get it working, but I'm stuck now. The driver exposes the following output ports: VGA, LVDS, Unknown-1, TV (there are no exposed physical connectors on the unit). According to Windows XP, which shipped with the units, the touch panel is connected to the LVDS port, so I disabled the rest of the connectors in xorg.conf explicitly, so they don't interfere with anything.

The vesa driver works fine by the way.

The screen is still black after all my attempts with the intel driver though. Any ideas what I should try to get something displayed?

Thanks




****** Update 1 ******

I'm getting "(EE) intel(0): underrun on pipe B!" errors in the X log periodically.

I also discovered the "--properties" switch for the "xrandr" command, and the related "--output LVDS --set" parameters. When I run "xrandr --properties", it says that the "BACKLIGHT" property is 0, and its range of values is (0,0)... Hmm... I checked the same on my laptop, and there the range is (0, 10781).

There's nothing in /sys/class/backlight on either the Eee Top or my laptop. The "xbacklight" command works on my laptop, and it does nothing on the Eee Top (displays "nan"). Switching the "BACKLIGHT_CONTROL" property to legacy gives me a range of (0,255) on the Eee Top, but changing the brightness value does nothing.

The good news is that the touchscreen works with the "evtouch" driver with little effort (link: [http://wiki.linuxmce.org/index.php/Asus_EeeTop](http://wiki.linuxmce.org/index.php/Asus_EeeTop)).


****** Update 2 ******

I got my hands on a EeePC 1000H, and saw that the brightness controls work on that thing. The eeepc-laptop module controls the backlight. So I tried adding the ATK0110 identified to that module, fingers crossed, hoping that it will work just like that. Well, no luck there. Now I'm really out of ideas, short of reverse engineering the ATK0110 driver that Asus ships for Windows.

---

### Post by radu.c on 2008-12-02
bump

---

### Post by diahrk on 2008-12-17
Well, sorry I can't help you.

I ordered an et1602 yesterday with the intnetion to install ubuntu on it. so I wonder: did it work out for you?? any recommendations?

would be happy to hear some good news
d

---

### Post by nglogic on 2008-12-21
I try to compile the last beta version from Intel:
xf86-video-intel 2.5.99.1 (2.6.0-rc1)
libdrm 2.4.2 (is required for xf86-video-intel 2.6.0)

And the problem is the same:  "Only a blank screem"

Any Ideas?


Note: I'm using kubuntu 8.10 with a Asus eee top 1602

---

### Post by sbaboc on 2009-01-29
hi all,
I received my eee top today, tried the usb live xubuntu: same problem as you guys!

Any news on this front?

Cheers,

---

### Post by diahrk on 2009-01-29
no news from my part. I gave up on that. at least I managed to get compositing going via metacity, under vesa. i don't miss the intel driver too much
cheers
dirk

---

### Post by sbaboc on 2009-01-30
After some googling on "(EE) intel(0): underrun on pipe B!", I see that "downgrading to xf86-video-intel-2.4.2-1 fixed the problem." (on an archlinux forum).

Sounds great! But how to do it on my usb key?

---

### Post by crj5 on 2009-02-13
Maybe the following page helps ? 
[http://wiki.linuxmce.org/index.php/Asus_EeeTop](http://wiki.linuxmce.org/index.php/Asus_EeeTop)

---

### Post by tormod on 2009-03-22
If the screen does not work out of the box with Jaunty, please file a bug as soon as possible.

---

### Post by Dulwithe on 2009-06-29
Were you able to get the vesa driver displaying at the proper resolution??

I can't even do that and have packed up my EEE Top ready to return it.

BTW, do you know of this link...

[http://www.eeepc.it/en/guida-installare-ubuntu-su-asus-eee-top-1602/](http://www.eeepc.it/en/guida-installare-ubuntu-su-asus-eee-top-1602/)

D.

---

### Post by ben72 on 2009-06-29
Hi, did you try the eee top on Ubuntu 9.04? I'm thinking of buying but I need to know of any problems before..

Thanks,

Ben

---

### Post by kat_ams on 2009-08-10
Using a site in Denmark I was able to find the right settings to get the ASUS ET1602 to work. Here is what you need to do:
*Everything has to be done in a terminal
Copy and paste is easiest.

[LIST=1]
[*]Install _Ubuntu Jaunty 9.04 Netbook Remixed_ in **SAFE MODE** from a USB stick. Follow the instructions on the Ubuntu homepage for Netbook Remixed on how to create the USB stick.
[*]Back up your original xorg.conf
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf~orig
```
[*]Download the **AsusET1602_xorg_touchscreen.tar.gz** attachment from this post
[*]Unpack the two files **xorg.conf** and **69.touchscreen.rules**
[*]Copy the xorg.conf file to /etc/X11/xorg.conf as sudo
```
sudo cp xorg.conf /etc/X11/xorg.conf
```
[*]Copy the 69.touchscreen.rules to /etc/udev/rules.d/69.touchscreen.rules
```
sudo cp 69.touchscreen.rules /etc/udev/rules.d/69.touchscreen.rules
```
[*]doublecheck to make sure you have the evtouch package installed
```
sudo aptitude update && sudo aptitude install evtouch
```
[*]reboot
```
sudo shutdown -r now
```
[*]You now have a working Asus EeeTop ET1602 with touchscreen functionality and proper screen resolution
[/LIST]

The contents of the attachment I will post separately for those that want to view the code 1st.

---

### Post by kat_ams on 2009-08-10
As promised here is the code

**xorg.conf** for the ASUS EeeTop ET1602

```

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier "Default Serverlayout"
	Screen 0 "Default Screen" 0 0
	InputDevice "Touch0"
EndSection


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"monitor-LVDS" "LVDS"
	Option		"monitor-LVDS-1" "LVDS-1"
	Option		"NoDCC"
	Option		"FramebufferCompression" "off"
EndSection


Section "InputDevice"
	Identifier "Touch0"
	Driver "evtouch"
	Option "device" "/dev/input/evtouch"
	Option "MinX" "1"
	Option "MinY" "1"
	Option "MaxX" "4096"
	Option "MaxY" "4096"
	Option "ReportingMode" "Raw"
	Option "Emulate3Buttons" "false"
	Option "Emulate3Timeout" "50"
	Option "SendCoreEvents" "on"
	Option "MoveLimit" "0"
EndSection

Section "Monitor"
	Identifier	"LVDS"
	Option		"Ignore" "True"
EndSection

Section "Monitor"
	Identifier	"LVDS-1"
	ModeLine	"1366x768" 76.00 1366 1386 1396 1560 768 770 773 793
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
 Subsection	"Display"
	Modes		"1366x768"
 EndSubsection
EndSection

```

---

### Post by kat_ams on 2009-08-10
Here is the file you need to activate the touchscreen.

One word of caution, the Calibrate Touchscreen option in the system settings does not work, it's not a problem because the touchscreen works perfectly as is. But please file a bug report in launchpad as requested when you click on the icon for Calibrate Touchscreen.

Here is the code you need to add to: please copy and paste it as the code is very specific. 
Note that:
Both ATTRS are followed by CURLY BRACES {}
and the 1st attribute is ONE B F D "1bfd"

This file is also NEW, you are adding it to the system.

/etc/udev/rules.d/**69.touchscreen.rules**

```

KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="1bfd", ATTRS{idProduct}=="1688", SYMLINK+="input/evtouch"

```

---

### Post by tormod on 2009-08-11
> **kat_ams said:**
> As promised here is the code

**xorg.conf** for the ASUS EeeTop ET1602


If you still need the ignore for the "LVDS" output in Karmic, please file a bug to bring it to the developers' attention.

---

### Post by kat_ams on 2009-10-24
I've been fighting with the ET1602 Revision C now for the last 3 weeks.
The motherboard is different on the ET1602C so this xorg.conf solution does not work for it.
I've brought it to the attention of Asus and they released a new bios that might have fixed the problem. But it didn't.

Here is the output of the xrandr of the ET1602
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1360 x 1360
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

```

If anyone has a clue as to how to get a working xorg.conf for the 1602C at 1366x768 LVDS I would be very grateful.

Right now the maximum I can get out of the screen is 1152x864

I was reading up on Karmic Koala. Apparently there is a new Intel video driver in the kernel that may solve these types of issues.

---

### Post by joe_newbie on 2009-11-29
For people with EEEtops:

Get the latest (Karmic) ubuntu netbook remix.
Install the latest touchscreen driver found here:

[https://launchpad.net/ubuntu/karmic/+package/xserver-xorg-input-evtouch](https://launchpad.net/ubuntu/karmic/+package/xserver-xorg-input-evtouch)

You should have a fully working EEETop with touchscreen working.  


Joe

---

### Post by sbceda on 2010-02-19
Hi Everyone,

I just got an ET1602C, and the modeline is different.  The solution is to get it with a software called PowerStrip and the instructions are posted here: [http://www.x.org/wiki/FAQVideoModes#ObtainingmodelinesfromWindowsprogramPowerStrip](http://www.x.org/wiki/FAQVideoModes#ObtainingmodelinesfromWindowsprogramPowerStrip)

Initially, xrandr reports:

[INDENT]Screen 0: minimum 320 x 200, current 1366 x 768, maximum 4096 x 4096
VGA1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3  
   640x480        59.9  
[/INDENT]
and so Ubuntu started in 800x600.

PowerStrip reported that the modeline would be:

[INDENT]"1366x768" 85.600 1366 1436 1579 1792 768 771 774 798 +hsync +vsync
[/INDENT]I changed a few lines in the xorg.conf posted by kat_ams.  Also I noticed that xrandr used the ID VGA1 instead of LVDS, and so I changed the references to LVDS to VGA also:

[INDENT]Section "ServerLayout"
    Identifier "Default Serverlayout"
    Screen 0 "Default Screen" 0 0
    InputDevice "Touch0"
EndSection


Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
    Option        "monitor-VGA" "VGA"
    Option        "monitor-VGA1" "VGA1"
    Option        "NoDCC"
    Option        "FramebufferCompression" "off"
EndSection


Section "InputDevice"
    Identifier "Touch0"
    Driver "evtouch"
    Option "device" "/dev/input/evtouch"
    Option "MinX" "1"
    Option "MinY" "1"
    Option "MaxX" "4096"
    Option "MaxY" "4096"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons" "false"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "on"
    Option "MoveLimit" "0"
EndSection

Section "Monitor"
    Identifier    "VGA"
    ModeLine    "1366x768" 85.600 1366 1436 1579 1792 768 771 774 798 +hsync +vsync
EndSection

Section "Monitor"
    Identifier    "VGA1"
    ModeLine    "1366x768" 85.600 1366 1436 1579 1792 768 771 774 798 +hsync +vsync
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    ModeLine    "1366x768" 85.600 1366 1436 1579 1792 768 771 774 798 +hsync +vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
 Subsection    "Display"
    Modes        "1366x768"
 EndSubsection
EndSection
[/INDENT]After a full re-start, Ubuntu was in 1366x768, and xrandr now reports:
[INDENT]Screen 0: minimum 320 x 200, current 1366 x 768, maximum 4096 x 4096
VGA1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       59.9*+
   800x600        60.3  
   640x480        59.9  
[/INDENT]There was a tiny sound coming from the monitor at first, but it goes away in a few seconds.

Now I need to figure out how to widen the scroll bars so I can actually touch them.

George

---

### Post by sbceda on 2010-02-23
By the way, to install EVTouch from Synaptic in Ubuntu 9.10, you need to include the universe set and change the server to "Server for United States."

---

