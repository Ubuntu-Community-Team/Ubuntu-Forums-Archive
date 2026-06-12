---
title: "Touchpad vertical scroll region is to wide"
date: 2009-04-06
forum: Hardware
---

### Post by carlosandcamy on 2009-04-06
Hello,

Hopefully this is an easy fix.  I just rolled from Ubuntu 8.10 to 8.04 and I've noticed that in 8.04 the vertical scrolling region is a whole lot wider.  So much so that it becomes annoying when the pointer gets on the workspace and changes my workspace.

Does anyone know of a previous post that might show me how to narrow the scrolling region of my touchpad on my laptop?  For the life of me I cannot find anything about this issue.

I am a newbie at Linux.

Thanks for your time

Running an HP Pavillion DV6000 on a dual boot from vista and Ubuntu.

---

### Post by Sam Lars on 2009-04-07
Have you checked out gsynaptics?  I've heard of it, never tried it.  It may help.

---

### Post by mxboy15u on 2009-04-07
I downloaded that and I got a message about setting something to "true" what does that mean?

---

### Post by Sam Lars on 2009-04-07
Setting what to true?

---

### Post by carlosandcamy on 2009-04-07
I found what I was looking for and will post as soon as I am at home.  Work is got everything firewalled and I can't get the weblink.

---

### Post by carlosandcamy on 2009-04-08
I found the following in a forum posted by a user named "the_blue_pill".  It is incredibly helpful and insightful.  Luckily for me he wrote it in a manner that I could understand what in the world I was doing.  Be forewarned, you will have to use the shell commands (i.e., terminal window)and also switch to the root user to edit the command file he mentions. Make sure you do a backup as he suggests, I too speak from experience now. 

If I haven't said it yet, THANK YOU blue_pill.

Below is what he posted.  Pick and choose what you want to change to your touchpad.  I only had to mess with the "VertScrollDelta" and the "right edge functions" to solve my problem.  But oh is there so much more you can do!.  And you can bet I'll be playing arround with it, just cause I can now. :p

Okay so what follows is what he posted, do follow the links he suggests.  Hopefully it will enlighten you as it did me.
***************************************************************
July 24th, 2006, 09:31 PM
Prologue: I actually posted this message before, but since people remained clueless on some points already addressed here I thought it might be more useful in the howto collection. Enjoy.
======================
I know there are several dozens of Howtos for touchpad woes but I thought one more wouldn't hurt. But seriously, to get mine working I had to make use of several of those guides, which generally were on specific details, such as how to turn off tapping etc. I thought a more general version for the Alps touchpad I'm using could be helpful. The guide is admittedly a 'bit' long but that's because I felt people would fare better if they knew the reasons for tweaking this parameter or that. I'm not an expert though, so feel free to correct or add to this guide. For the record, I have an Inspiron 8600 and running breezy. Here goes:

-------Preliminary checks: Know thy enemy
First off, check if the evdev module is available and loaded.
Type:
lsmod |less
and scroll down to see if evdev is there.

Next, look in the 'devices' file with your favourite text editor
vi /proc/bus/input/devices
to see if your touchpad is detected correctly, you should find several related lines like:
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
As you can see, the touchpad is correctly identified here. Write down the handlers line, we'll use this information later.
As an additional tidbit, the serial and USB mice should show different handlers, e.g. for mine:
I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse0 event1 ts0
...
I: Bus=0003 Vendor=0d62 Product=a100 Version=0300
N: Name="Darfon USB Optical Mouse"
P: Phys=usb-0000:00:1d.0-1/input0
H: Handlers=mouse2 event4 ts2
Sadly, the additional devices are handled somewhat arbitrarily, and this causes problems as I'll refer to later on.

Open up the xorg log file:
vi /var/log/Xorg.0.log
and see if the synaptics driver is loaded. In mine, I see:
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
compiled for 4.2.0, module version = 1.0.0
Module class: XFree86 XInput Driver
ABI class: XFree86 XInput driver, version 0.3

Normally, there should be no problem with these preliminary checks. If there is, refer to the following discussion for possible solutions:

[http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt](http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt)


----------------Delving into xorg.conf: The beast within
Almost every parameter related to the touchpad performance is (or will be. once you're done) has to be in /etc/X11/xorg.conf
Make sure that you backup this file before doing anything! It's very easy to lose track of the different blocks, lines and entries and screw the file so badly that your X session won't start! Experience speaks here...
Anyway once you've backed it up, open up your xorg.conf
sudo vim /etc/X11/xorg.conf

You should first find an entry of Section "InputDevice" with driver "synaptics". This is where we make most of our changes. If this is the first time you're editing this section, you'll see the default settings. In mine I see the following lines:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Looks short and elegant. Except that (surprise, surprise!) it doesn't work. My edited version is below. I'll try to explain in detail what the changes mean.
Section "InputDevice"
Identifier "Alps Touchpad"
Driver "synaptics"
Option "AlwaysCore"
Option "Protocol" "event"
Option "Device" "/dev/input/event2"
Option "LeftEdge" "120"
Option "RightEdge" "910"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "10"
Option "FingerHigh" "15"
Option "MaxTapTime" "300"
Option "MaxTapMove" "110"
Option "ClickTime" "0"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.95"
Option "AccelFactor" "0.015"
Option "EdgeMotionMinSpeed" "40"
Option "EdgeMotionMaxSpeed" "40"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "SHMConfig" "false"
EndSection




First line under the InputDevice header is the identifier. Don't bother much about it - it doesn't matter what it says BUT it should be exactly the same as what is written towards the end of the file, in the Section "ServerLayout". So if you name your touchpad 'foopad' in the section above you should change it to that in the ServerLayout section too. Thus mine has the following line:
Section "ServerLayout"
...
InputDevice "Alps Touchpad"
EndSection

The second line is the driver to be used. That's fine too. Some people have recommended to include the line
Load "synaptics"
in the Section "Module" upstairs but mine works happily without it.

The next three lines are the most diabolical of all, and in general information available in the net is vague or worse, contradictory. Suffice to say that in my configuration, these three lines have to be EXACTLY what I posted here or the touchpad won't work. On a brighter note, if you get these three lines to work correctly, the rest is really easy and victory shall be yours. So if my configuration doesn't work straight out of the post for you, you'll need to play with them, i.e. edit xorg.conf then restart x (ctrl-alt-backspace). Repeat, rinse, next cycle and so on. To see if the touchpad configuration communicates successfully with the operating system, edit the option
Option "MaxTapTime" "300"
to
Option "MaxTapTime" "0"
This will disable tap-to-click if linux is at all aware of your changes. And yes that is how you disable tapping, but if your other parameters are optimized, you really don't need to disable this feature. Read on.

Simply put I don't know what the "AlwaysCore" option means. You can try to sort it out from this link:

[http://www.tldp.net/HOWTO/Wacom-Tablet-HOWTO-5.html](http://www.tldp.net/HOWTO/Wacom-Tablet-HOWTO-5.html)

Scroll down to 5.12 Device Modes extension and see if you can make some sense out of it.

The protocol option refers to the method used by the kernel to cope with the input. Ideally, auto-dev should take care of everything but it doesn't. So I set it to 'event'

The Device option should point to the handler for the touchpad. Recall that these handlers are reported in the /proc/bus/input/devices file
Mine had event2 as the handler so that's what ended up in my xorg.conf
Though I haven't tried, it is mentioned that one could also use the other handler(s) e.g. 'mouse1' for this line.


---------------- Optimizing parameters: The coup de grace
Hopefully, now linux is aware that you're trying to do something with the touchpad and is reacting to it. Don't let the plethora of following options intimidate you: many are not essential and you'll be pleasantly surprised to see that you can actually teach your touchpad some neat tricks. Mine didn't support scrolling under windows for example and now it does!

For in depth explanation of the parameters, refer to

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)
[http://www.tctwest.net/~mlewis00/XF86Config-4.synaptics](http://www.tctwest.net/~mlewis00/XF86Config-4.synaptics)

I'll just cover the basics. The left,right, bottom and top edge parameters - as you might guess - set the coordinates for the corners of the touchpad. More importantly, these determine where the edges and therefore edge events, such as scrolling, start. For instance when I declared the right edge of the touchpad as 840, the scroll region occupied almost a third of the pad, and I had to expand the right edge to above 900 for comfortable motion.

The infernal: " selecting and tapping by mistake while moving the cursor " problem is embedded in the MaxTapMove option. It means the maximum amount of movement 'noise' that is allowed when a tap is detected. Setting this lower will preclude tapping when there is motion.

The tap-and-drag functionality can be enabled by the MaxTapTime parameter. You might have noticed that when you attempt to drag something, your finger lingers on the pad, so a higher time is required to allow the detection of the second 'drag' tap.

VertScroll and HorizScroll delta are self explanatory. If scrolling is enabled, for instance by: Option "UpDownScrolling" "1", these determine the scrolling distance while your finger is sliding down the pad.

The MinSpeed, MaxSpeed and AccelFactor work in cohort to determine the speed of your pointer. Adjust these to your liking.

The EdgeMotion speed options dictate the rate of effects that occur when you're at the edge. e.g. when you drag an icon across the screen and you reach an edge, the icon will appear to 'jump'. The higher the parameter value, the bigger that jump is.

Finally the option: Option "SHMConfig". Supposedly the effect of this is to toggle userspace configuration through an interface such as ksynaptics. It didn't work for me but you might give it a shot and set it to 'true'


---------------------The glitch: A parting shot
Well it wouldn't be linux if everything just worked would it? As I mentioned before, when you plug in a usb mouse, linux nicely assigns new handlers to it and your event numbers remain intact. When you plug it out, the entry is deleted as can be seen from the devices file. Now, when you boot your linux kernel WITH the usb mouse plugged in, linux decides to assign the portable usb mouse the first event number for an inexplicable reason, thus changing the event numbers. So the handlers for the touchpad in my example become mouse1, event3 and so on. Why a detachable device is given priority over a permanently fixed touchpad is beyond my comprehension. Worse, the entry doesn't disappear when you unplug the usb mouse, or even when you restart X! You have to restart linux get rid of the entry.

Fortunately there is a workaround. Just keep your mouse unplugged while booting and attach it only after you get to the login. That way everything works proper.

-----------


So that's it. It's really sad that a treatise is needed to get something as elementary as a touchpad to work but I guess that's how it goes. Hopefully dapper has better handling.
vBulletin® v3.8.1, Copyright ©2000-2009, Jelsoft Enterprises Ltd.

***************************************************************

##################################################################################
#
# This file has been modified to demonstrate the configuration of the Synaptics
# Touchpad driver for the XFree86 X Window System. The original file that this is
# based upon is the standard XF86Config-4 file installed with the Debian Sarge
# xserver-xfree86 package. If you find any mistakes or know of any additional
# information that may be useful to include please email them to me at:
# <mlewis0000000 at netscape.net> .
#
# Modifications copyright (c) 2005, M. Glenn Lewis, All Rights Reserved
# The modifications that I have made to this program are covered by the terms  
# of the GNU General Public License:
# 
# 	This program is free software; you can redistribute it and/or modify
# 	it under the terms of the GNU General Public License as published by
# 	the Free Software Foundation; either version 2 of the License, or
# 	(at your option) any later version.
#
# 	This program is distributed in the hope that it will be useful,
# 	but WITHOUT ANY WARRANTY; without even the implied warranty of
# 	MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# 	GNU General Public License for more details.

# 	You should have received a copy of the GNU General Public License
# 	along with this program; if not, write to the Free Software Foundation,
# 	Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA
#
# Other copyrights may apply and the copyrights for the original document that
# my modifications are based upon may be found on a standard Debian Sarge
# installation at '/usr/share/doc/xserver-xfree86/copyright'.
#
# You may modify / distribute this program as you wish provided that the original
# copyright notices remain intact in any distribution of this program or any work
# derived from it and provided that you comply with all of the terms of the copyrights
# that protect this program.
#
#####################################################################################
#
# Note: This file will function as a direct replacement for /etc/X11/XF86Config-4,
# although you may want to use it as a guide only because it is comparatively
# large and difficult to modify.
#
# For documentation concerning the installation of the xfree86-driver-synaptics
# package, configuration of the evdev interface, etc., see the documentation for the
# package at /usr/share/doc/xfree86-driver-synaptics/.
#
#####################################################################################
#
# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"vbe"
	Load	"synaptics"			# Tell X to load the synaptics driver.
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

#Section "InputDevice"				# My configuration works better without the configured mouse
						# although some prefer to leave it installed.
#	Identifier	"Configured Mouse"	# Remove the '#' characters at the beginning of the lines to
#	Driver		"mouse"			# use this device. Also see ' Section "ServerLayout" ' below
#	Option		"CorePointer"		# if you enable this device.
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

### Start synaptics configuration section ###	# Documentation at:
						# /usr/share/doc/xfree86-driver-synaptics/README.Debian
						#
Section "InputDevice"				# Start section.
						#
	Identifier  		"TouchPad"	# Name doesn't matter - needs to be the same as in
						# Section "ServerLayout" below.
						#
	Driver  		"synaptics"	# Name of driver to load (synaptics or alps or ...).
						#
	Option			"CorePointer"	# 'AlwaysCore' or 'CorePointer' (see docs).
						#
	Option 	"Device"  	"/dev/psaux"	# Mouse device (see docs).
						#
	Option	"Protocol"	"auto-dev"	# Mouse protocol (see docs).
						#
#	Option	"Repeater"	"/dev/ps2mouse"	# Device to repeat mouse events to.
						#
################################################# Shared memory configuration (SHMConfig ) allows configuration of the 
						# touchpad from user space. This has possible security implications -
						# see documentation.
						#
						# IMPORTANT! You may find that certain GUIs (KDE) will call the
						# synaptics driver after XF86Config-4 has been parsed and cause all of
						# the values you have programmed via XF86Config-4 to be reset to the
						# default driver values or to different values. If you find that your
						# XF86Config-4 configuration values seem to have no effect, set
						# SHMConfig to 0 (off) until you can create a script to load your
						# values via the 'synclient' program or until you can disable the
						# offending applet or program.
						# 
						# Example: For KDE you can run (as the root user) the command
						# 'apt-get --purge remove ksynaptics' to remove the synaptics
						# control center module and then your XF86Config-4 settings will be
						# preserved (provided that you have no other modules or programs that
						# configure the driver upon loading the KDE GUI).
						#
	Option	"SHMConfig"		"1"	# Leave off (0) until the touchpad is working correctly in X,
						# then turn on (1)to enable configuration from X applets or Xterm.
						# This eliminates X apps from interfering with XF86Config-4 tweaks.
						# Or leave on (1) if you prefer to use 'synclient' from within X to
						# configure the touchpad.
						# If you leave it on you may need to create a script that runs
						# after the X Server and session manager have finished loading
						# to restore your preferred settings, since some GUI environments
						# configure these settings automatically (i.e. after the X windows
						# system has loaded the driver and parsed the XF86Config-4 file).
						#
################################################# The LeftEdge, RightEdge, TopEdge, and BottomEdge parameters define
						# the edges of a rectangle within which all touches, taps, and gestures
						# will be interpreted normally. This rectangle is defined in units
						# which are derived from the way that the touchpad is manufactured.
						# To understand the units used, the coordinate system could be
						# viewed as a grid of wires embedded in the surface of the touchpad
						# (6143 wires in the horizontal [X] direction and 6143 wires in the
						# vertical [Y] direction), with each wire capable of reporting the
						# proximity of a finger to it and / or finger pressure [Z].
						# The standard touchpad is measured in units starting from the left
						# edge in the 'X' direction (0-6143 units), and from the bottom edge
						# in the 'Y' direction (0-6143 units). The edges are the actual edges
						# of the touchpad before it is mounted in the computer - the bezel
						# that the touchpad is mounted in limits the actual finger contact area
						# to an area that is usually less than the maximum on all sides. This
						# means that the left edge of the bezel may be 1000 units from the
						# actual edge of the touchpad. Therefore, it is necessary to define a
						# rectangle that tells the synaptics driver that your finger is
						# approaching the edge of the bezel and will be unable to continue
						# motion in the current direction. This will allow the driver to
						# initiate special features such as Edge Motion(tm) or scrolling.
						#
						# The LeftEdge, RightEdge, TopEdge, and BottomEdge parameters define a 
						# rectangle where finger motion will emulate normal mouse motion - any 
						# motion outside of this rectangle will cause different behavior (such 
						# as scrolling, or continuation of current motion at a certain rate
						# [Edge Motion(tm)]). Set these values to a value that accommodates
						# the width of your finger between the edge of the defined rectangle
						# and the bezel to start with, and then adjust as desired.
						#
						# NOTE: The Range figures given below are how much adjustment is
						# allowed for by the 'synclient' program, although there may be no 
						# effect when these values are set beyond a certain limit.
						#
	Option	"LeftEdge"      	"1500"	# Range 0-10000	Units (pad coordinates)	Standard value 1700
						# Distance from the left edge of the touchpad to the left edge of the
						# defined rectangle.
						#
	Option	"RightEdge"     	"5350"	# Range 0-10000	Units (pad coordinates)	Standard value 5300
						# Distance from the left edge of the touchpad to the right edge of the
						# defined rectangle.
						#
	Option	"TopEdge"       	"1500"	# Range 0-10000	Units (pad coordinates)	Standard value 1700
						# Distance from the top edge of the touchpad to the top edge of the
						# defined rectangle.
						#
	Option	"BottomEdge"    	"4450"	# Range 0-10000	Units (pad coordinates)	Standard value 4200
						# Distance from the top edge of the touchpad to the bottom edge of the
						# defined rectangle.
						#
################################################# The next two values work together - lower values make the touchpad
						# more sensitive to touching and tapping, but some difference is
						# needed between them.
						#
						# Low threshold of pressure for finger detection - values below this
						# threshold will cause the finger contact to be considered ended.
	Option	"FingerLow"		"15"	# Range 0-255	Units (pressure)	Standard value 25
						# This value must be approximately 10-20 units lower than the value of
						# 'FingerHigh' - otherwise instability and / or spurious generation of 
						# tap events will be generated.
						#
						# High threshold of pressure for finger detection - values above this
						# threshold will cause the finger contact to be considered valid.
	Option	"FingerHigh"		"25"	# Range 0-255	Units (pressure)	Standard value 40
						# Lower values increase the touchpad's sensitivity to touch (provided
						# that 'FingerLow' is set at a value that is less than 'FingerHigh').
						#
################################################# The next three values work together to determine whether a tap event
						# will be generated or not.
						#
						# Maximum finger contact time for the contact to be considered a tap.
						# Lower values make the touchpad less 'sensitive' to taps - higher
						# values may cause tap events to be generated for normal finger touch
						# and release gestures.
	Option	"MaxTapTime"		"180"   # Range 0-1000	Units (ms)		Standard value 180
						# '0' = no tap-to-click
						#
						# Maximum amount of finger movement allowed for the tap to be
						# considered valid - if the finger moves more then this amount from
						# the time of contact to time contact ends, the tap event will not be
						# generated.
	Option	"MaxTapMove"		"220"	# Range 0-2000	Units (relative)	Standard value 220
						# '0' = eliminate single finger tap-to-click but allow two
						# and three finger tap-to-click
						#
						# Maximum time allowed between successive taps for the taps to be
						# interpreted as a double-click, triple-click, etc.
	Option	"MaxDoubleTapTime"	"150"	# Range 0-1000	Units (ms)		Standard value 150
						#
################################################# The amount of time between the button-up and button-down events
						# that the X windows system generates in response to a tap event.
	Option	"ClickTime"		"60"	# Range 0-1000	Units (ms)		Standard value 60
						#
################################################# Speed up tapping for single clicks.
	Option	"FastTaps"		"1"	# Range 0-1	Units Boolean		Standard value 1
						# Use fast taps - 0 = false, 1 = true
						#
################################################# Time within which the left and right mouse buttons must be pressed
						# for a middle-button event to be generated - i.e. allowable time
						# between when one of the buttons is pressed and the other is pressed.
	Option	"EmulateMidButtonTime"	"75"	# Range 0-1000	Units (ms)		Standard value 75
						#
################################################# Vertical and Horizontal sensitivity.
						# Distance the finger must move to generate a scroll event. Lower values
						# will result in faster scrolling.
						#
	Option	"VertScrollDelta"	"100"	# Range 0-1000	Units (relative)	Standard value 100
						# Amount of change in vertical position since last packet was sent
						# to driver.
						#
	Option	"HorizScrollDelta"	"110"	# Range 0-1000	Units (relative)	Standard value 110
						# Amount of change in horizontal position since last packet was sent
						# to driver.
						#
################################################# Factors to translate finger motion to cursor motion.
						#
						# This factor is used when the finger is moving slowly.
	Option	"MinSpeed"		"0.01"	# Range 0-1.0	Units (relative)	Standard value 0.01
						# Decrease this value to increase the ability to precisely position
						# the mouse cursor.
						#
						# This factor is used when the finger is moving rapidly.
	Option	"MaxSpeed"		"0.10"	# Range 0-1.0	Units (relative)	Standard value 0.10
						# Increase this value to increase the distance traveled by the mouse
						# cursor when the finger is moved rapidly across the touchpad.
						#
						# Factor by which MinSpeed or MaxSpeed is multiplied.
	Option	"AccelFactor"		"0.0075"# Range 0-0.2	Units (relative)	Standard value 0.0075
						# Increase this value to increase the speed of cursor movement at both
						# MinSpeed and MaxSpeed speeds.
						#
################################################# Edge Motion(tm) - Continuation of the motion that was occurring when
						# the finger reached the edge of the touchpad (i.e. the bezel).
						#
	Option	"EdgeMotionMinZ"	"30"	# Range 1-255	Units (relative)	Standard value 30
						# Edge Motion(tm) minimum pressure - pressure at which the minimum
						# scroll speed is set.
						#
	Option	"EdgeMotionMaxZ"	"160"	# Range 1-255	Units (relative)	Standard value 160
						# Edge Motion(tm) maximum pressure - pressure at which the maximum
						# scrolling speed is set.
						#
	Option	"EdgeMotionMinSpeed"	"100"	# Range 0-1000	Units (relative)	Standard value 1
						# Edge Motion(tm) minimum speed.
						#
	Option	"EdgeMotionMaxSpeed"	"150"	# Range 0-1000	Units (relative)	Standard value 150
						# Edge Motion(tm) maximum speed.
						#
						# If false, Edge Motion(tm) is only used for dragging and scrolling -
						# if true, Edge Motion(tm) is also used for normal mouse movements.
	Option	"EdgeMotionUseAlways"	"0"	# Range 0-1	Units Boolean		Standard value 0
						# Always use Edge Motion(tm) - 0 = false, 1 = true
						#
################################################# Whether to use the Up / Down scrolling buttons as scroll buttons or
						# special buttons.
	Option	"UpDownScrolling"	"1"	# Range 0-1	Units Boolean		Standard value 1
						# If 1, the Up / Down buttons generate button 4 and button 5 events,
						# respectively. If 0, the Up / Down buttons generate a double-click
						# and a button 2 event, respectively.
						#
################################################# Turn touchpad on or off.
	Option	"TouchpadOff"		"0"	# Range 0-3	Units N/A		Standard value 0
						# If 1, the touchpad is off - if 0, the touchpad is on, if 3, the
						# touchpad has tapping disabled.
						#
################################################# Turn auxiliary mouse / joystick on or off.
	Option	"GuestMouseOff"		"1"	# Range 0-1	Units Boolean		Standard value 1
						# If 1, auxiliary mouse is off - if 0, auxiliary mouse is on.
						#
################################################# Use locked drags to extend drag gestures beyond the edges of the
						# touchpad.
	Option	"LockedDrags"		"0"	# Range 0-1	Units Boolean		Standard value 0
						# If 1, a drag gesture does not end until the pad is tapped again -
						# if 0, a drag gesture ends when the finger is lifted from the
						# touchpad.
						#
################################################# Description of values for the various 'Button' tap actions.
						# 0 = No action, 1 = Left Button, 2 = Middle Button, 3 = Right Button
						# There may be other values defined but these are the standard ones.
						#
						# It may be necessary to increase the value of MaxTapMove to a greater
						# value to obtain the '??CornerButton' events reliably.
						#
						# Button event that is generated when the right-top corner of the
						# touchpad is single-tapped.
	Option	"RTCornerButton"	"3"	# Range 0-12	Units N/A		Standard value 3
						#
						# Button event that is generated when the right-bottom corner of the
						# touchpad is single-tapped.
	Option	"RBCornerButton"	"3"	# Range 0-12	Units N/A		Standard value 3
						#
						# Button event that is generated when the left-top corner of the
						# touchpad is single-tapped.
	Option	"LTCornerButton"	"0"	# Range 0-12	Units N/A		Standard value 0
						#
						# Button event that is generated when the left-bottom corner of the
						# touchpad is single-tapped.
	Option	"LBCornerButton"	"0"	# Range 0-12	Units N/A		Standard value 0
						#
						# Button event to report for single-finger tap detected outside
						# of a corner or specially defined area.
	Option	"TapButton1"		"0"	# Range 0-12	Units N/A		Standard value 1
						#
						# Button event to report for two-finger tap detected outside
						# of a corner or specially defined area.
	Option	"TapButton2"		"1"	# Range 0-12	Units N/A		Standard value 2
						#
						# Button event to report for a three-finger tap detected outside
						# of a corner or specially defined area.
	Option	"TapButton3"		"0"	# Range 0-12	Units N/A		Standard value 3
						#
################################################# Use circular dragging gestures to emulate a scroll-wheel.	
	Option	"CircularScrolling"	"0"	# Range 0-1	Units Boolean		Standard value 0
						# If on, circular scrolling is on - if off, circular scrolling is off.
						#
						# Angle of finger movement required to generate a scroll event.
	Option	"CircScrollDelta"	"0.05"	# Range .01-3.0	Units (radians)		Standard value 0.05
						#
						# Defines the area(s) of the touchpad which will initiate a circular
						# scroll if CircScrollDelta radians of angular movement is detected.
	Option	"CircScrollTrigger"	"0"	# Range 0-8	Units (relative)	Standard value (User pref)
						# 0=All Edges, 1=Top Edge, 2=Top Right Corner, 3=Right Edge,
						# 4=Bottom Right Corner, 5=Bottom Edge, 6=Bottom Left Corner,
						# 7=Left Edge, 8=Top Left Corner
						#
################################################# Whether the touchpad is circular - if so, the LeftEdge, RightEdge,
						# TopEdge, and BottomEdge parameters define an ellipse instead of a
						# rectangle.
	Option	"CircularPad"		"0"	# Range 0-1	Units Boolean		Standard value 0 (or User pref)
						# If 0, the touchpad is rectangular - if 1 the touchpad is 'circular'.
						#
################################################# Palm contact detection.
	Option	"PalmDetect"		"1"	# Range 0-1	Units Boolean		Standard value 1 (or User pref)
						# Detect palm contact - 0 = off, 1 = on
						#
	Option	"PalmMinWidth"		"10"	# Range 0-15	Units (pad coordinates)	Standard value (10)
						# Minimum width of contact area to trigger palm detection.
						#
	Option	"PalmMinZ"		"200"	# Range 0-255	Units (relative)	Standard value (200)
						# Minimum contact pressure to trigger palm detection.
						#
################################################# Locked scrolling speed.
	Option	"CoastingSpeed"		"20"	# Range 0-20	Units (relative)	Standard value 10
						# Speed that the window scrolls if you start the scroll by dragging
						# your finger on the edge of the touchpad and then 'throw' the scroll
						# with your finger.
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
	VideoRam	128000
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	HorizSync	28-96
	VertRefresh	50-75
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Color LCD"
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
#	InputDevice	"Configured Mouse" "CorePointer"
#	InputDevice	"TouchPad" "AlwaysCore"
	InputDevice	"TouchPad" "CorePointer"	# Comment this line out to use the Configured Mouse
							# as CorePointer and the TouchPad as AlwaysCore - also
							# uncomment the above two lines in that case.
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Sam Lars on 2009-04-08
Wow, that is an excellent and thorough explanation.  Thanks for sharing.

---

### Post by bhagwad on 2009-04-29
I would suggest that you don't modify the xorg.conf file. Apparently it's deprecated. The latest advice for Jaunty 9.0.4+ is to use hal fdi files. Here is the explanation: [http://bhagwad.com/blog/2009/04/configure-alps-touchpad-in-ubuntu-904-jaunty-jackalope.html](http://bhagwad.com/blog/2009/04/configure-alps-touchpad-in-ubuntu-904-jaunty-jackalope.html)

---

