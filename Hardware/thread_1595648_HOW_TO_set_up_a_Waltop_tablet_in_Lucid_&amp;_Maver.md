---
title: "HOW TO set up a Waltop tablet in Lucid &amp; Maverick"
date: 2010-10-13
forum: Hardware
---

### Post by Favux on 2010-10-13
**& Natty & Oneiric & Precise**

Last updated:  May 29, 2012

**[SIZE="3"]Preliminaries[/SIZE]**
Waltop tablets are often re-branded by the various Tablet Vendors.  To determine if you have a Waltop tablet enter in a terminal:
```
xinput list
```
One of the devices labeled pointer should have WALTOP in the <device name>.  The Vendors usually give the re-branded tablet their own model name.  To determine the actual underlying "model" or Product ID enter in a terminal:
```
lsusb
```
In the output should be a line containing Waltop and the Waltop Vendor ID = 172f.  It will be immediately followed by the Product ID, separated from the Vendor ID, by a colon.  For example:
```
Bus 007 Device 003: ID 172f:0038 Waltop International Corp. Genius G-Pen F509
```
In this case the Product ID = 0038.


**[SIZE="3"]Sources[/SIZE]**
**[DIGImend SourceForge site]("http://sourceforge.net/projects/digimend/")**
**[DIGImend mediawiki]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend")**

See "**Attention Waltop tablet in Lucid & Maverick** users" near the top of the **[LinuxWacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1")**.
**[Graphic Tablet working in 5 steps!!]("http://ubuntuforums.org/showpost.php?p=9252390&postcount=1")** by al.do
**[How to make your Genius G-pen F610 Tablet work on Ubuntu 10.04 Lucid Lynx]("http://ubuntuforums.org/showpost.php?p=9573142&postcount=1")** by AlexDS
**[waltop weirdness]("http://ubuntuforums.org/showthread.php?t=1594056")**

Releases prior to Lucid:
**[Tablet Buttons don't work (Genius GPEN F610)]("http://ubuntuforums.org/showthread.php?t=1261407")**
**[Still can't get waltop/medion graphics tablet to work, can't build drivers in karmic]("http://ubuntuforums.org/showthread.php?t=1326789")**


**[SIZE="3"]Ubuntu Release Specific Notes[/SIZE]**
**Oneiric** (11.10):  Setup should be the same as with Maverick and Natty only requiring a custom 52-waltop-on-wacom.conf in /etc/X11/xorg.conf.d as with them.  However things are in a bit of a state of flux and some Waltop tablets may in fact work better on the new 2.6 version of evdev X driver that comes with Oneiric.  See the [Tablet support status]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status") page on the DIGImend mediawiki.  So you may want to try the xf86-input-evdev driver if your tablet is not behaving well with the xf86-input-wacom driver.

**Maverick** (10.10) & **Natty** (11.04):  The Waltop tablets work with the Wacom X driver, xf86-input-wacom.  Ubuntu calls the xf86-input-wacom driver the xserver-xorg-input-wacom package.  However the stylus side buttons do not work correctly with Maverick's 2.6.35 kernel.  The two side buttons can not be given different settings. They do work in Natty's 2.6.38 kernel thanks to Nikolai Kondrashov's kernel patches.

**Lucid** (10.04):  The Waltop tablets are actually suppose to be using xf86-input-wacom (the xserver-xorg-input-wacom package).  Just like they did with linuxwacom in the long, long ago (i.e. Intrepid (8.10)).  Unfortunately the Waltop usb driver in the hid part of the kernel does not quite support the tablet using the xf86-input-wacom X driver wacom_drv.so. Patches have been submitted by Nikolai Kondrashov to the kernel that partially fixes this with Maverick and gets everything working with Natty. In the meantime you can get the tablet functioning surprisingly well with the WizardPen driver.  The main difference is pressure is linear instead of on a bezier curve like with the wacom driver.  You can use the application, e.g. Gimp, to adjust pressure a little.


**[SIZE="3"]Precise Pangolin (12.04) & Oneiric Ocelot (11.10) & Natty Narwhal (11.04) & Maverick Meerkat (10.10)[/SIZE]**
**I.  Verify the Wacom X driver xf86-input-wacom is installed**
Check in Synaptic Package Manager that the Ubuntu package that contains xf86-input-wacom, xserver-xorg-input-wacom, is installed (green box checked).  Or check in the Software Center.  It should be by default.

**II. Create a USB snippet to match the WALTOP to the Wacom X driver**
The default usb tablet snippet in the 50-wacom.conf in /usr/share/X11/xorg.conf.d will look something like:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

```
As you can see the WALTOP keyword is commented out.  You want to add WALTOP back into the match line.  But since files in /usr/share/X11/xorg.conf.d are placed there by Ubuntu and may be overwritten during an update it is recommended you not make any user-specific configuration changes there.

Instead user-specific changes are suppose to go in /etc/X11/xorg.conf.d.  So we'll create a file called **52-waltop.conf** and place the Waltop match to the wacom driver there.
```

Section "InputClass"
	Identifier "Waltop buttons"
	MatchProduct "WALTOP"
        MatchIsKeyboard "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "Waltop scroll"
	MatchProduct "WALTOP"
	MatchIsPointer "off"
	MatchIsKeyboard "off"
	MatchIsTouchpad "off"
	MatchIsTablet "off"
	MatchIsTouchscreen "off"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "Waltop pen"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
        # Apply custom Options below this line.

EndSection

```
The MatchIsTablet match is used so only the Waltop's digitizer/stylus is matched, not its pad buttons.  This is because other Waltop devices (/dev/input) exported from the kernel such as tablet buttons are not supported by xf86-input-wacom and should instead be on xf86-input-evdev.  Use:
```
gksudo gedit /etc/X11/xorg.conf.d/52-waltop-on-wacom.conf
```
to create and edit the 52-waltop.conf file.  Save, Close, and reboot.  You may need to reboot several times for things to "shake out".

You may need to create the /etc/X11/xorg.conf.d directory if it is not already there.  To do so run this command:
```
sudo mkdir /etc/X11/xorg.conf.d
```

For more details see [**52-waltop.conf**]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-wacom#52-waltop.conf") on the DIGI*mend* wiki.  But basically the "Waltop scroll" snippet is to enable scroll for your tablet's multifuction dial or jog wheel if it has one.  And the "Waltop buttons" snippet is to reclaim the keyboard events for evdev if you have a 50-wacom.conf with Waltop in the usb snippet rather than in the new stand alone Waltop snippet.  The new Waltop stand alone snippet is in xf86-input-wacom-0.14+ but has been backported into Precise's xf86-input-wacom-0.14.0.  Oneiric's xf86-input-wacom-0.12.0 has the Waltop keyword in the usb snippet in 50-wacom.conf.  So Oneiric requires that the keyboard events (buttons, volume, etc.) be reclaimed from Wacom for evdev.  Natty still has the Waltop match commented out in its default xf86-input-wacom-0.11.10.

**III.  Consider updating xf86-input-wacom**
There are more changes being made to the Wacom X driver to make it more non-wacom tablet friendly.  You may want to consider cloning the git repository.  If you do you can use step "II. Install Xorg'sxf86-input-wacom tar or clone the git repository for Lucid, Maverick, Natty, & Oneiric (the X driver)" at the [Bamboo Pen & Touch HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

**IV.  Using the xsetwacom script .xsetwacom.sh**
To gain finer control over your styus with the wacom drivers you can use a script of xsetwacom commands.  The script is an example and you may need to change the xsetwacom Parameter names depending on you version of xsetwacom.  See the Linux Wacom Project's mediawiki [HOW TOs]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO") and [Waltop Tablet Set Up]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Waltop_Tablet_Set_Up").

To set it up to auto-start, download the attached file,  and rename it .xsetwacom.sh (or whatever you want) and place it in your home directory or create a *bin* folder to place scripts in.  Remember it will be a hidden file.  You can remove the . in front so the file isn't hidden if placing it in a *bin* directory.  Making it hidden is just to prevent directory clutter.  To enable the xsetwacom commands in the .xsetwacom.sh file to apply to Xserver through a reboot you enter in a terminal:
```
chmod +x ~/.xsetwacom.sh
```
or you could right click on the file and in Properties, in the Permission tab, check Execute as program.  Then go to System->Preferences->Startup Applications and click on add and for the command write "sh /home/yourusername/.xsetwacom.sh" (without the quotes).  You can also change your settings on the fly using the xsetwacom parameters in a terminal.  They only apply during the current session since they are runtime commands.  Remember to use the "device name" that:
```
xinput list
```
returns for your stylus.

If you are happy with the driver's default settings there is no need to reapply them with the script.  Just comment (#) out those lines.  But leave those lines in so you have a list of valid modifications available.

**V.  Dual and Multi-Monitor Set.**
See **[HOW TO Setup a Wacom Tablet with Multi-Monitors in Maverick and Natty]("http://ubuntuforums.org/showthread.php?t=1656089")** or [Dual and Multi-Monitor Set Up]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up") on the mediawiki.

**VI.  Pre-patched Kernels for Waltop Support.**
Kernels are now available for Oneiric and Precise that add more support and new Waltop models.  So if yours isn't working check the DIGI*mend* site for the status of your tablet.  The kernels are available here in [DIGI*mend* Files]("http://sourceforge.net/projects/digimend/files/kernel-packages/kernel-patches-5/").  Instructions are on the DIGI*mend* mediawiki page "[Kernel packages]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_packages")" with further details on the [DIGI*mend* blog]("http://sourceforge.net/apps/wordpress/digimend/2012/04/17/first-kernel-packages-are-out/").

**VII.  Waltop Kernel Patches - Fix Both Stylus Buttons Work the Same in Maverick.**
According to Nikolai Kondrashov:
> The issue is the Waltop HID report descriptor. It doesn't describe buttons correctly. Please try applying my patches for 2.6.36 kernel [1], or use 2.6.37, which has them integrated.
The patch set is on his [DIGI*mend* project site]("http://digimend.sourceforge.net/#proj-kernel-patches").  Plenty of goodies on the site.  It includes a patch set for kernel 2.6.35 (Maverick) as well as 2.6.32 (Lucid) and 2.6.36.  Instructions for patching the kernel are on "[HOW TO Add Support for KYE, UC-logic, and Waltop Tablets in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1946486")".


**[SIZE="3"]Lucid Lynx (10.04)[/SIZE]**
**I.  Install the WizardPen driver**
To get the WizardPen X driver download and install the appropriate xserver-xorg-input-wizardpen package from DoctorMO's (Martin Owens) PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages)

Or add the PPA to Software Sources:  System-Administration > Software Sources > Other Software tab > +Add > then in the "APT line" enter:  ppa:doctormo/xorg-wizardpen 

**II.  Configure your Waltop tablet through the wizardpen.conf**
Replace the 70-wizardpen.conf with this modified one:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
In **Lucid** use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/70-wizardpen.conf

```
In **Maverick** (if you prefer not to use the Wacom X driver) use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
Save, close, and reboot.

**III.  Available Options**
You can add any of the following Options below the [Driver  "wizardpen"] line in the first snippet of the modified 70-wizardpen.conf.  The driver should automatically set these for you.  However you may want to change some of them, especially Rotation, DebugLevel, TPCButton, and Mode, depending on your preference.: 
```
# first four Options set automatically, unless you want to use wizardpen-calibrate
Option  "TopX"  "0"
Option  "TopY"  "0"
Option  "BottomX"  "17782"
Option  "BottomY"  "10584"

Option  "TopZ"  "0"  # minumum pressure, default is 20?
    # not sure that the default is 20; you should able to treat it as a pressure threshold
    # (or "ZThreshold") using values like 5, 10, or 20 if stylus seems too sensitive

Option  "BottomZ"  "511"  # or "1023"; maximum pressure
    # depending on whether the tablet has 512 or 1024 pressure levels

Option  "Rotate90"  "0"  # or "1"
    # 1 rotates tablet 90 degrees

# following two options set automatically
Option  "ScreenX"  "1280"
Option  "ScreenY"  "1024"

Option  "DebugLevel"  "0"  # or "1" to turn debug on
    # Not sure how many debug levels are available, at a guess 0 - 12

Option  "MouseSpeed"  "30"
    # don't know the allowed range or which are useful

Option  "MouseAccel"  "0"  # or "1"
    # 1 turns acceleration on, useful if you are using the tablet as a "mouse"
    # i.e. using [Option "Mode" "Relative"]

Option  "TPCButton"  "on"  # or "off"
    # on is "tip + buttons" while off is "hover mode" i.e. buttons only

Option  "Mode"  "Absolute"  # or "Relative"
    # I believe this is an available option, "Relative" would make the tablet
    # function like a "mouse"

```
At this point some of these Options are educated guesses.  So experimentation needed and use with caution.

As an example of using the Options in the first snippet:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
        Option  "TopZ"  "20"  # pressure threshold
        Option  "TopX"  "0"
        Option  "TopY"  "0"
        Option  "BottomX"  "17782"
        Option  "BottomY"  "10584"
EndSection
```
**Note**:  Some Waltops need a pressure threshold over 50 to work correctly on the WizardPen driver.

**IV.  Calibrate your tablet** (if needed) using **wizardpen-calibrate**
You need to determine the event # for your tablet.  In a terminal enter:
```
cat /proc/bus/input/devices
```
In the output you'll see something like:
```
H: Handlers=kbd mouse1 event4
```
Using your event # enter in a terminal:
```
wizardpen-calibrate /dev/input/event4
```
Follow the instructions and use the data from the yellow rectangle in the appropriate Options (see above).
* thanks to al.do & AlexDS

**Edit (11-18-10)**:  I was using the linuxwacom ClickForce default and range in the script below for stylus based on a device with 1,024 pressure levels.  Howeveer xf86-input-wacom does things differently.  The default ClickForce for the stylus is FILTER_PRESSURE_MAX/75.  Whatever pressure levels a device reports is normalized to 2048 levels.  So even for the Waltop stylus, with I think 1024 pressure levels (let me know if I'm wrong), the ClickForce line should look something like:
```
xsetwacom set "WALTOP International Corp. Slim Tablet stylus" ClickForce "27"  # default is 27, 0-2047
```
They renamed ClickForce to Threshold.  So now, if you have xf86-input-wacom 0.10.9+, it is something like:
```
xsetwacom set "WALTOP International Corp. Slim Tablet stylus" Threshold "27"  # default is 27, 0-2047
```
See the commit "[xsetwacom: rename ClickForce to Threshold]("http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=1bfe863e1abb1bb731edce375ade675d484e5d65")"

**Edit (12-7-10)**:  Updated Sample Waltop .xsetwacom.sh.  First version had 37 downloads.

**Note**:  Since they do change the xsetwacom Parameter names, defaults, and ranges from time to time you should check in *man xsetwacom* or [Xsetwacom]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom") for the current names and values.

---

### Post by Favux on 2010-10-13
**Materials for Possible Additional Configuration in Lucid**

Enter in a terminal 'man wizardpen' after installing the driver.  Notice that it is pretty dated.
> **THE MANPAGE FOR WIZARDPEN**:

**WizardPen(4)**

**NAME**
wizarpen - WizardPen tablet input driver

**SYNOPSIS**
Section "InputDevice"
Identifier "Tablet"
Driver "wizardpen"
Option "Device" "devpath"
...
EndSection
...
Section "ServerLayout"
...
InputDevice "Tablet"
...
EndSection

**DESCRIPTION**
wizardpen is an Xorg input driver for WizardPen Tablet devices...

The wizardpen driver functions as a pointer input device, and may be
used as the X server's core pointer. THIS MAN PAGE NEEDS TO BE FILLED
IN.

**SUPPORTED HARDWARE**
What is supported...
WizardPen tablets

**CONFIGURATION DETAILS**
Please refer to xorg.conf(5) for general configuration details and for
options that can be used with all input drivers. This section only
covers configuration details specific to this driver.

Option "TopX" "val"
Allows the use of an alternative left edge location.

val should be equal to the x value of the new left edge

Option "TopY" "val"
Allows the use of an alternative top edge location.

val should be equal to the y value of the new top edge

Option "TopZ" "val"
Allows the use of an alternative minimum pressure.

val should be equal to the value of the new minimum pressure

Option "BottomX" "val"
Allows the use of an alternative right edge location.

val should be equal to the x value of the new right edge

Option "BottomY" "val"
Allows the use of an alternative bottom edge location.

val should be equal to the y value of the new bottom edge

Option "BottomZ" "val"
Allows the use of an alternative maximum pressure.

val should be equal to the value of the new maximum pressure

**SEE ALSO**
Xorg(1), xorg.conf(5), xorgconfig(1), Xserver(1), X(7).

**AUTHORS**
Authors include... Edouard TISSERANT Zachary Cornelius

X Version 11 wizardpen 0.7.4 WizardPen(4)
* thanks to keevee09

It's possible additional configuration could also be done through X.  If you enter 'man xinput' in a terminal there are a few parameters that may be worth looking at:
> xinput get-feedbacks device_name
Display the feedbacks of device_name. Uses XGetFeedbackCon&#8208;
trol(3).

xinput set-pointer device_name
Switch device_name in core pointer. Uses XChangePointerDe&#8208;
vice(3).

xinput set-mode device_name ABSOLUTE|RELATIVE
Change the mode of device_name. Uses XSetDeviceMode(3).

xinput set-ptr-feedback device_name threshold num denom
Change the acceleration of device_name. Uses XChangeFeedback&#8208;
Control(3).

xinput set-integer-feedback device_name index value
Change the value of an integer feedback of device_name. Uses
XChangeFeedbackControl(3).

xinput set-button-map device_name map button 1 [map button 2 [...]]
Change the button mapping of device_name. Uses XSetDeviceBut&#8208;
tonMapping(3).

xinput set-int-prop device_name property format value
Sets an integer property for the device. Appropriate values
for format are 8, 16, or 32, depending on the property.

xinput test [-proximity] device_name
Register all extended events from device_name and enter an end&#8208;
less loop displaying events received. If the -proximity is
given, ProximityIn and ProximityOut are registered. 

First figure out what your device is called.  Enter in a terminal:
```
xinput --list
```
Then using the device name in quotes enter:
```
xinput list-props "WALTOP International Corp. Slim Tablet"
```
> Device 'WALTOP International Corp. Slim Tablet':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268 ):    1.000000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    10.000000
* thanks to icodemonkey
```
xinput get-feedbacks "WALTOP International Corp. Slim Tablet"
```
> 1 feedback class
PtrFeedbackClass id=0
accelNum is 2
accelDenom is 1
threshold is 4
* thanks to keevee09  He also ran:
```
xinput test "WALTOP International Corp. Slim Tablet" > tablet_feedback.txt

```
> The text file was quite long :) but scrolling through I found it gave max/min values for

a[0] of 9496/500 # x values I guess
a[1] of 5932/312 # y values
a[2] of 1023/0 # z values - pressure

---

### Post by Favux on 2010-10-13
Reserved.

---

### Post by Favux on 2010-12-08
Hi everyone,

Updated and corrected the Waltop .xsetwacom.sh (xsetwacom commands script).  Also added some more, and hopefully more useful comments into the script. Please read through them.

---

### Post by aapo4 on 2011-03-14
(I started this on bamboo -topic, but this might be better topic)

I have Aiptek 14000u Media Tablet, which is re-branded Waltop.

When I just plug-it to the Ubuntu-10.10, it is not using wacom-driver at all (if I read logs properly). I can move mouse cursor with pen and make clicks. Pen has two buttons, so I think it is possible to make clicks button1+button2+button3. Even I try remapping, both modifier buttons send same (button2 or button3).
With 'xinput test' I can see pressure is detected.

But when I try to use pen with applications it doesn't work. I have tested Gimp and MyPaint. They both have default that pressure is not used. (disabled), and can be changed to 'screen' or 'window'. If I change it to the screen, pen is not then drawn anything. Error messages to console are:

(gimp:2466): Gdk-CRITICAL **: gdk_input_update_axes: assertion `first_axis >= 0 && first_axis + axes_count <= gdkdev->info.num_axes' failed

/usr/share/mypaint/gui/main.py:54: GtkWarning: gdk_input_update_axes: assertion `first_axis >= 0 && first_axis + axes_count <= gdkdev->info.num_axes' failed

*
With wacom driver
I change /usr/share/X11/xorg.conf.d/50-wacom.conf and rebooted. According to the /var/log/Xorg.0.log (attached) it is now using wacom (0.10.99 from git)
Loading /usr/lib/xorg/modules/input/wacom_drv.so
compiled for 1.9.2.901, module version = 0.10.99

With this driver pen is not working, when I touch anywhere on the tablet, mouse cursor jumps to top-left-corner and doesn't move.
With xinput test I can see all motion events are the very same:
motion a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 

Am I understood correctly that long term plan is that every tablets uses same 'wacom-driver'? So must useful is try to get this tablet working with wacom?

---

### Post by Favux on 2011-03-14
> Am I understood correctly that long term plan is that every tablets uses same 'wacom-driver'?
I don't know about every tablet, but certainly the Waltops.
> I can move mouse cursor with pen and make clicks. Pen has two buttons, so I think it is possible to make clicks button1+button2+button3. Even I try remapping, both modifier buttons send same (button2 or button3).
That's due to a bug in the 2.6.35 and 2.6.36 kernels.  It's fixed in the 2.6.37 kernel by Nikolai Kondrashov.  I think he has a fix on his [DIGImend project site]("http://digimend.sourceforge.net/#proj-kernel-patches") for the 2.6.35 kernel, but I'm not sure I'd use it.
> With 'xinput test' I can see pressure is detected.  But when I try to use pen with applications it doesn't work.
Well we know it worked for earlier 2.6.35 kernels and the default xf86-input-wacom-0.10.8.  So something may have been broken in the recent kernel update or in xf86-input-wacom after 0.10.8.

However your *xinput list* shows:
> &#9116;   &#8627; WALTOP International Corp. Media Tablet eraser	id=10	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet pad	id=11	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet stylus	id=12	[slave  pointer  (2)]
But you don't have an eraser or pad.  Even though the Xorg.0.log shows them happily being set up.  Do you see the same 3 input tools with *xsetwacom list*?  Maybe that's causing the problem with Gimp and MyPaint.  Let's try eliminating eraser and pad with a different match.  Change the match line from:
```
	MatchProduct "Wacom|WALTOP|WACOM"

```
to
```
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "WALTOP International Corp. Media Tablet stylus"

```
Hopefully evdev won't pick up the eraser and pad.

---

### Post by aapo4 on 2011-03-15
Attached Xorg-log when wacom-driver is not used, but waltop.

With this settings pointer can be used, and xinput test detects pressure, but gimp not.

xinput list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                       	id=8	[slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                       	id=9	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet 	id=10	[slave  pointer  (2)]

```

(Note: there are not word stylus, like with wacom driver)

---

### Post by Favux on 2011-03-15
> Attached Xorg-log when wacom-driver is not used, but waltop.
Don't understand what you are telling me.

That Xorg.0.log shows the tablet/stylus on the evdev driver, matched by the "evdev tablet catchall" snippet.  You definitely don't want the evdev driver for a stylus.

A short cut to find out what driver a device is on is to use the "device name" in quotes from *xinput list* with list-props.
```
xinput list-props "WALTOP International Corp. Media Tablet"
```
in the current xinput list output.  Or to check if it is on the wacom driver you could use *xsetwacom list*.

---

### Post by aapo4 on 2011-03-15
Ok, know I understand.

So currently only way how I can use tablet at all is use it with evdev driver.

*
When I add MatchProduct "Wacom|WALTOP|WACOM" ( on /usr/share/X11/xorg.conf.d/50-wacom.conf) I get stylus, eraser and pad. But mouse cursor is not moving, but it jumps to the upper left corner.
```
xsetwacom list
WALTOP International Corp. Media Tablet eraser	id: 10	type: ERASER    
WALTOP International Corp. Media Tablet pad	id: 11	type: PAD       
WALTOP International Corp. Media Tablet stylus	id: 12	type: STYLUS

```

I tried: MatchProduct "WALTOP International Corp. Media Tablet stylus"
(written exactly same way than xinput/xsetwacom list shows it.) But then wacom driver is not used, but evdev instead.

---

### Post by aapo4 on 2011-03-15
I got eraser and pad out from list with these:

```
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
        MatchProduct "Wacom|WALTOP|WACOM"
#       MatchProduct "Wacom|WACOM|Hanwang"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
    Identifier     "no eraser or pad"
    MatchProduct   "eraser|pad"
    Option         "Ignore" "on"
EndSection
```


But mouse cursor is not moving.
Attached Xorg.log

---

### Post by Favux on 2011-03-15
Well that seemed to work in Xorg.0.log.  It's saying:
```
[    24.770] (II) XINPUT: Adding extended input device "WALTOP International Corp. Media Tablet stylus" (type: STYLUS)
```
And you see the stylus in xinput list and xsetwacom list?

If so we're back to a dead battery in the stylus.  You said it wasn't working in Windows either.

---

### Post by aapo4 on 2011-03-15
```
xsetwacom list       
WALTOP International Corp. Media Tablet stylus	id: 10	type: STYLUS

```
Yes, this time without eraser and pad.

It didn't worked under Windows and I got new piece of hardware for warranty. This device is quickly tested under Windows, mouse cursor is moving and clicking works (not sure any pressure stuff).

And device is 'working' with evdev driver under Ubuntu. So I think it is not dead battery.

---

### Post by Favux on 2011-03-16
OK, you've got me stumped.  The Xorg.0.log seems to show the stylus being placed on the Wacom driver correctly.  The *xsetwacom list* command shows the stylus on the Wacom X driver.  So it doesn't appear the Ignore Option blocked the stylus from the driver.  It should be working.  But the stylus doesn't move the pointer arrow?

Have you tried the stylus script attached to the HOW TO?  See if that kick starts anything.  Are you using the default xf86-input-wacom 0.10.8 for Maverick or did you update it?  The script needs to be updated for 0.10.11 or later.

---

### Post by maslot on 2011-03-16
I found a solution for strange behaviour of WALTOP tablet with ID 172f:0037 (I own Aiptek Hyperpen Mini)
If your tablet works like in this post [http://ubuntuforums.org/showpost.php?p=10209416&postcount=21](http://ubuntuforums.org/showpost.php?p=10209416&postcount=21) you can try my magic.
Find a young virgin and black cat, stand in moonlight and wisper this spell:
```

sudo su
lsusb -v

```I checked it on two computers and it works for me.

---

### Post by Favux on 2011-03-16
I think that is a kernel issue although it may have been an issue with xf86-input-wacom-0.10.8.

I checked if the tablet models are in xf86-input-wacom's wcmUSB.c and they are:
```
	{ WALTOP_VENDOR_ID, 0x501, 100000, 100000, &usbBamboo    },
```
for
```
[    4.618767] generic-usb 0003:172F:0500.0003: input,hidraw2: USB HID v1.10 Mouse [WALTOP International Corp. Media Tablet] on usb-0000:00:1d.1-1/input0
```
and for Waltop tablet with Vendor ID=172f and Product ID=0037 (172f:0037; Aiptek Hyperpen Mini)
```
	{ WALTOP_VENDOR_ID, 0x37,  80000,  80000, &usbGraphire4  },
```
I wonder if 172F would be a problem instead of 172f, in other words could it be case sensitive?


Edit:  Nope, that isn't it.  In xf86WacomDefs.h it is already:
```
#define WALTOP_VENDOR_ID 0x172F
```

---

### Post by aapo4 on 2011-03-21
I'm using wacom-driver 0.10.99 from git. Mouse cursor is not moving with pen.

I modified script a little bit:
```
DEVICE_NAME="WALTOP International Corp. Media Tablet stylus"

xsetwacom set "$DEVICE_NAME" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "$DEVICE_NAME" RawSample "2"  # data pt.s filtered, default is 2, 0-100 
xsetwacom set "$DEVICE_NAME" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "$DEVICE_NAME" PressureCurve "5 10 90 95" # Bezier curve, default is 0,0,100,100
xsetwacom set "$DEVICE_NAME" TabletPCButton "on"  # stylus tip + button, or "off" for hover mode
xsetwacom set "$DEVICE_NAME" Mode "Absolute"  # or Relative cursor movement

```

Are these values sane? E.g. what mean 'Enable Touch'? Should area not be square? Should there been entry 'Wacom Screen Area'?
```

xinput list-props "WALTOP International Corp. Media Tablet stylus"
Device 'WALTOP International Corp. Media Tablet stylus':
	Device Enabled (128):	1
	Coordinate Transformation Matrix (130):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (274):	0
	Device Accel Constant Deceleration (275):	1.000000
	Device Accel Adaptive Deceleration (276):	1.000000
	Device Accel Velocity Scaling (277):	10.000000
	Wacom Tablet Area (300):	0, 0, 16383, 16383
	Wacom Rotation (301):	0
	Wacom Pressurecurve (302):	5, 10, 90, 95
	Wacom Serial IDs (303):	1280, 0, 2, 0
	Wacom Capacity (304):	-1
	Wacom Pressure Threshold (305):	27
	Wacom Sample and Suppress (306):	4, 2
	Wacom Enable Touch (307):	0
	Wacom Hover Click (308):	1
	Wacom Enable Touch Gesture (309):	0
	Wacom Touch Gesture Parameters (310):	50, 20, 250
	Wacom Tool Type (311):	"STYLUS" (296)
	Wacom Button Actions (312):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (313):	0, 0

```

xinput test "WALTOP International Corp. Media Tablet stylus" prints same row each time I touch drawing area with pen:
motion a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
(But it detects when I touch it)

---

### Post by artspace on 2011-03-29
Sorry for my English... I'm from Taiwan. I have a strange problem with my newly bought Waltop based tablet/screen digitizer (branded ACCU) in which my stylus pointer remains "tip pressed" all the time (please see the attached pict).

I actually followed the instruction on Favux's post and installed wizardpen driver on my 10.0.4 Lucid (amd64 version) which had the xserver-xorg-input-wacom installed and used to work absolutely great with my Wacom Intuos 2 tablet (it was unplugged right before I installed the ACCU screen). 

The lsusb shows:
```
Bus 004 Device 002: ID 172f:0051 Waltop International Corp.
```

xinput-list:
```
&#9116;   &#8627; WALTOP International Corp. PEN-INPUT DEVICE	id=12	[slave  pointer  (2)]
```

The cat /proc/bus/input/devices:
```
I: Bus=0003 Vendor=172f Product=0051 Version=0110
N: Name="WALTOP International Corp. PEN-INPUT DEVICE"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input7
U: Uniq=
H: Handlers=mouse2 event7 
B: EV=1b
B: KEY=c03 70001 0 0 0 0
B: ABS=ffffff000100000f
B: MSC=10

```

and my 70-wizardpen.conf is (already modified and calibrated):
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event7"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver "wizardpen"
	Option		"Device"	"/dev/input/event7"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"7200"
	Option		"BottomY"	"5400"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver ""
EndSection
```

Any suggestion? I think I am almost to get it working (or maybe not...).

Many thanks!

---

### Post by Favux on 2011-03-29
Hi artspace,

Let's try this first:
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   MatchProduct "WALTOP|Waltop"
   MatchDevicePath "/dev/input/event*"
   Driver "wizardpen"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"7200"
	Option		"BottomY"	"5400"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   MatchProduct "WALTOP|Waltop"
   MatchDevicePath "/dev/input/mouse*"
   Option "Ignore" "yes"
EndSection
```

---

### Post by artspace on 2011-03-30
> **Favux said:**
> Hi artspace,

Let's try this first:
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   MatchProduct "WALTOP|Waltop"
   MatchDevicePath "/dev/input/event*"
   Driver "wizardpen"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"7200"
	Option		"BottomY"	"5400"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   MatchProduct "WALTOP|Waltop"
   MatchDevicePath "/dev/input/mouse*"
   Option "Ignore" "yes"
EndSection
```

Thank you so much for such prompt reply!!!

BTW, I have tried it but there's no change...:(

---

### Post by Favux on 2011-03-30
OK, post the output of:
```
xinput list
```
and then using the "device name" from that for the stylus/tablet the output of:
```
xinput list-props "device name"
```

---

### Post by artspace on 2011-03-30
> **Favux said:**
> OK, post the output of:
```
xinput list
```
and then using the "device name" from that for the stylus/tablet the output of:
```
xinput list-props "device name"
```
xinput list:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; GASIA GASIA USB KB Pro                  	id=9	[slave  pointer  (2)]
&#9116;   &#8627; PS/2+USB Mouse                          	id=11	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. PEN-INPUT DEVICE	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; GASIA GASIA USB KB Pro                  	id=8	[slave  keyboard (3)]
    &#8627; HID 04d9:a02a                           	id=10	[slave  keyboard (3)]

```
and xinput list-props is:
```
Device 'WALTOP International Corp. PEN-INPUT DEVICE':
	Device Enabled (125):	1
	Device Accel Profile (244):	0
	Device Accel Constant Deceleration (245):	1.000000
	Device Accel Adaptive Deceleration (247):	1.000000
	Device Accel Velocity Scaling (248):	10.000000

```

I've just found an interesting thing... it's kind of working in GIMP if I set the extended input device of WALTOP to screen (pls see attached pict), but I still can't use the pointer to click on any functional icons nor menus....

---

### Post by Favux on 2011-03-30
The output is a little strange.  I don't think it is on the WizardPen driver or the evdev driver.  It looks like it is on a mouse driver.

We need to look at Xorg.0.log in /var/log.  Right click on it and compress it with Create Archive.  Attach it to your next post with Manage Archives below.

Did you install the WizardPen driver with DoctorMO's PPA and reboot?

---

### Post by artspace on 2011-03-30
> **Favux said:**
> The output is a little strange.  I don't think it is on the WizardPen driver or the evdev driver.  It looks like it is on a mouse driver.

We need to look at Xorg.0.log in /var/log.  Right click on it and compress it with Create Archive.  Attach it to your next post with Manage Archives below.

Did you install the WizardPen driver with DoctorMO's PPA and reboot?
Yes I used the DoctorMO's PPA and rebooted. The xorg.0.log is attached.

Thanks again!

---

### Post by Favux on 2011-03-30
Sure.

The Xorg.0.log looks good:
```
(II) config/udev: Adding input device WALTOP International Corp. PEN-INPUT DEVICE (/dev/input/event7)
(**) WALTOP International Corp. PEN-INPUT DEVICE: Applying InputClass "evdev tablet catchall"
(**) WALTOP International Corp. PEN-INPUT DEVICE: Applying InputClass "wizardpen"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.7.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event7"
(--) WALTOP International Corp. PEN-INPUT DEVICE: MaxX:7200 MaxY:5400 MaxZ:1023
(--) WALTOP International Corp. PEN-INPUT DEVICE: aspect ratio:1.33:1
(**) WALTOP International Corp. PEN-INPUT DEVICE is in absolute mode
(II) WALTOP International Corp. PEN-INPUT DEVICE: ScreenX = 1280, ScreenY = 1024
(**) WALTOP International Corp. PEN-INPUT DEVICE: TopX                   = 0
(**) WALTOP International Corp. PEN-INPUT DEVICE: TopY                   = 0
(**) WALTOP International Corp. PEN-INPUT DEVICE: BottomX                = 7200
(**) WALTOP International Corp. PEN-INPUT DEVICE: BottomY                = 5400
(**) WALTOP International Corp. PEN-INPUT DEVICE: TopZ    (min pressure) = 0
(**) WALTOP International Corp. PEN-INPUT DEVICE: BottomZ (max pressure) = 1023
(**) WALTOP International Corp. PEN-INPUT DEVICE: always reports core events
(II) XINPUT: Adding extended input device "WALTOP International Corp. PEN-INPUT DEVICE" (type: WizardPen Tablet)
(II) WALTOP International Corp. PEN-INPUT DEVICE Increment: 5
(II) config/udev: Adding input device WALTOP International Corp. PEN-INPUT DEVICE (/dev/input/mouse2)
(**) WALTOP International Corp. PEN-INPUT DEVICE: Ignoring device from InputClass "wizardpen ignore mouse dev"
```
Was that the entire *xinput list-props "WALTOP International Corp. PEN-INPUT DEVICE"* output?

Let's try setting a minimum pressure threshold:
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   MatchProduct "WALTOP|Waltop"
   MatchDevicePath "/dev/input/event*"
   Driver "wizardpen"
	Option		"TopZ"		"15"  # pressure threshold
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"7200"
	Option		"BottomY"	"5400"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   MatchProduct "WALTOP|Waltop"
   MatchDevicePath "/dev/input/mouse*"
   Option "Ignore" "yes"
EndSection
```

---

### Post by artspace on 2011-03-30
Thank you so much Favux!

I've tried the minimum pressure threshold but still no change....:(:(

Yes that was the entire xinput list-props "WALTOP International Corp. PEN-INPUT DEVICE" output.... looks very short right?

It's about noon time here in Taiwan and I guess it's must be mid-night in your place...

---

### Post by Favux on 2011-03-30
Yep, I'm about to pass out.  :)

Well try increasing it to 5% and 10%, ~50 and ~100.  I doubt that will work though.

You seem to be getting a button press without a release.  So either your tablet doesn't work quite right with the WizardPen driver or the usb hid kernel driver for the Waltop tablet changed a little recently.  Try rebooting several times and see if that "shakes" things out.

You are correct to set the Gimp extended input to screen for the stylus.  That's what it should be for it to work in Gimp or Inkscape. But it should allow you to select icons and menus.

Another thought is to try the Aiptek driver (xserver-xorg-input-aiptek).  A couple of Waltop users have reported it works for them.  The Aiptek driver package doesn't come with a 50-aiptek.conf though.  You have to make one.

---

### Post by artspace on 2011-03-30
I'll try the Aiptek driver later and will report the result here...

This digitizer works just fine with Window XP and Mac OSX, so I believe there must be some way to get it work on Ubuntu!

Thank you again Favux and it is so good having you here to help us!!

**Have a nice sleep~~~~:D

---

### Post by artspace on 2011-03-30
It works now!!!!:biggrin::biggrin:

I increase the pressure to above 50 and everything works great now!

Thank you Favux!! You've saved my life!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=187525&stc=1&d=1301467071[/IMG]

---

### Post by Favux on 2011-03-30
Excellent!  :)

How far above 50 did you go?  In other words what number worked?

And thank you for the feedback.  Now we know some Waltop tablets on the WizardPen driver need a pressure Threshold (TopZ) above 50.  So over 4.8% of the available pressure levels.

The Wacom driver defaults to 27 but it first normalizes pressure levels to 2047.  So it is set at 1.3%.  And that might be too low for some Waltops.

---

### Post by artspace on 2011-03-30
> **Favux said:**
> Excellent!  :)

How far above 50 did you go?  In other words what number worked?

And thank you for the feedback.  Now we know some Waltop tablets on the WizardPen driver need a pressure Threshold (TopZ) above 50.  So over 4.8% of the available pressure levels.

The Wacom driver defaults to 27 but it first normalizes pressure levels to 2047.  So it is set at 1.3%.  And that might be too low for some Waltops.
I've tried 20, 25, 30, 40, 45, 50, 60, 85 and 100 - only 50+ worked (I didn't try 41-49). I'm using 60 right now since 50 can still get into a mess sometimes.

I wonder how this value would affect the drawing quality... I think it should be set as low as possible.

---

### Post by Favux on 2011-03-30
It shouldn't make a very noticeable difference.  Only the very lightest strokes won't be recorded.  The pressure levels for the WizardPen driver are linear, so setting the threshold at 60 cuts out the first 61 levels (0-60).  You still have the levels 61 to 1023 left.

---

### Post by Supergnu on 2011-04-08
Good evening,

i bought an aiptek tablet 600u premium II today and installed and configured the wacom driver as you instructed me.
the tablet works for about 5 minutes but then the led blinks and i have to reboot to get the driver work again

---

### Post by Favux on 2011-04-08
Hi Supergnu,

What release of Ubuntu are you using?  Lucid or Maverick?

What is the output of:
```
xinput list
```
in a terminal?

Does your Xorg.0.log in /var/log show anything happening when the tablet fails?

---

### Post by Supergnu on 2011-04-09
thx for your reply!

Im using Ubuntu Maverick

xinput --list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet  	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]
```

The log doesn't change, it's like the tablet doesn't recognize the pen after about 3 minutes

---

### Post by Supergnu on 2011-04-09
There was a short circuit in my pen right before the inductor.
I fixed it, but now i have the problem, that after i right click with the pen i can't move the curser and i have to take the pen away so that it works again.
Except this, everthing works properly.

---

### Post by Favux on 2011-04-09
And the Xorg.0.log shows the stylus is on the Wacom X driver?  Let's verify that with the output of:
```
xinput list-props "WALTOP International Corp. Slim Tablet"
```
in a terminal.

Doesn't sound like a problem with the battery in the stylus.  Could something be interrupting the usb signal?  And then the hotplug doesn't go correctly.  You should see a hotplug event in the Xorg.0.log if that is what's happening.  Make sure the usb cable is firmly seated on both ends.  Is it directly plugged into a usb port or is it on a hub?

---

### Post by Supergnu on 2011-04-09
```
Device 'WALTOP International Corp. Slim Tablet':
	Device Enabled (139):	1
	Coordinate Transformation Matrix (141):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (268):	0
	Device Accel Constant Deceleration (269):	1.000000
	Device Accel Adaptive Deceleration (270):	1.000000
	Device Accel Velocity Scaling (271):	10.000000
	Evdev Reopen Attempts (260):	10
	Evdev Axis Inversion (272):	0, 0
	Evdev Axis Calibration (273):	<no items>
	Evdev Axes Swap (274):	0
	Axis Labels (275):	"Abs X" (265), "Abs Y" (266), "Abs Pressure" (267), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Button Labels (276):	"Button Left" (142), "Button Middle" (143), "Button Right" (144), "Button Wheel Up" (145), "Button Wheel Down" (146), "Button Horiz Wheel Left" (147), "Button Horiz Wheel Right" (148), "Button Side" (263), "Button Extra" (264), "Button Unknown" (261), "Button Unknown" (261), "Button Unknown" (261), "Button Unknown" (261)
	Evdev Middle Button Emulation (277):	2
	Evdev Middle Button Timeout (278):	50
	Evdev Wheel Emulation (279):	0
	Evdev Wheel Emulation Axes (280):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (281):	10
	Evdev Wheel Emulation Timeout (282):	200
	Evdev Wheel Emulation Button (283):	4
	Evdev Drag Lock Buttons (284):	0
```

Hotplugging works fine.
It's directly plugged in, i tried 2 ports => same result

---

### Post by Favux on 2011-04-09
That was useful.  The list-props command shows your tablet is on the evdev X driver and not the Wacom driver.  So something is going wrong with your match in the wacom.conf.  Can you post your current 50-wacom.conf?

---

### Post by Supergnu on 2011-04-09
Thank you Favux!

I reinstalled the wacom driver a few times and forgot to change the 50-wacom.conf

Now it works like a charm!

---

### Post by PCNetSpec on 2011-04-09
Hi Supergnu... I helped someone install a Aiptek Tablet 600U Premium II, a couple of weeks ago.

It seemed to be VERY sensitive to having the correct MatchProduct line, in 50-wacom.conf, and it being case sensitive.

We eventually ditched  MatchProduct in favour of a MatchVendor line of:

MatchVendor "Waltop|WALTOP|waltop"

Full instructions here:
[http://linuxforums.org.uk/general-help-advice/aiptek-tablet-driver-for-linux-is-confusing/msg40092/#msg40092](http://linuxforums.org.uk/general-help-advice/aiptek-tablet-driver-for-linux-is-confusing/msg40092/#msg40092)

just in case they might help.

[EDIT]
Heh... too late, glad you got it sorted

@ **Favux**, just wanted to add my thanks, I'd never have been able to work this out without all your tutorials, and forum threads.

---

### Post by Supergnu on 2011-04-09
Yes that was the problem but i already fixed it

Thank you anyway!

---

### Post by Favux on 2011-04-09
Good!  :)


Hi PCNetSpec,

Thank you for the thanks.  Glad they helped you.

---

### Post by aapo4 on 2011-05-04
Just for records: I got my "Aiptek 14000u Media Tablet" (re-branded Waltop) working with Natty (11.04), without hazzle.

I don't know what was relevant changes. With Maverick I used xorg-edgers-PPA, which is not needed anymore.

---

### Post by emaydubya on 2011-06-14
Waltop Success at Last!!

After countless hours (40 in the last couple of weeks) over at least 2 years. Several breakages through updates/upgrades and then more hours.

I have never got the Waltop to work properly. Either the stylus works well and no buttons, buttons and bad stylus or some other issue always gave problems.
Very recently, the stylus was just weird, several new problems arose.

But now it's all fixed. I fixed it with a hammer. It's all bent and in pieces and destined for the tip.
This is the best thing to happen to this pad since I got it. I now don't have to think about how easy it was when it actually worked. I don't have to come back here and scour posts looking for the "Thing" that makes it work. I am so over it.

I will now decline any graphics work and go back under my rock and on the dole.

---

### Post by LordOfDragons on 2011-07-11
Just a little question. I'm using here a TB7300 with the wacom driver (I tried also wizardpen). Stylus works without a problem with pressure sensitivity and all. The only thing not working at all are the buttons all around the tablet and the two wheels. There are a total of 34 buttons around the pad (K1 to K34) including the wheels and none of them works. This bothers me as with GIMP it would be nice to assign those buttons to the tools in the toolbox for faster selection. The following I gathered:

```
Device 'WALTOP International Corp. Media Tablet':
        Device Enabled (121):   1
        Coordinate Transformation Matrix (123): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (240):     0
        Device Accel Constant Deceleration (241):       1.000000
        Device Accel Adaptive Deceleration (242):       1.000000
        Device Accel Velocity Scaling (243):    10.000000
        Evdev Axis Inversion (501):     0, 0
        Evdev Axis Calibration (502):   <no items>
        Evdev Axes Swap (503):  0
        Axis Labels (504):      "Abs X" (498), "Abs Y" (499), "Abs Pressure" (500)
        Button Labels (505):    "Button Unknown" (497), "Button Unknown" (497), "Button Unknown" (497), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
        Evdev Middle Button Emulation (506):    0
        Evdev Middle Button Timeout (507):      50
        Evdev Wheel Emulation (508):    0
        Evdev Wheel Emulation Axes (509):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (510):    10
        Evdev Wheel Emulation Timeout (511):    200
        Evdev Wheel Emulation Button (512):     4
        Evdev Drag Lock Buttons (513):  0
```

Thus at least the wheels are listed as existing values yet they do not work. Any ideas what could be done there? Any ideas how to get the 34 other buttons to work? Can I somehow test if the events are actually generated by the kernel driver?

---

### Post by Favux on 2011-07-11
Hi LordOfDragons,

The hot keys or hot buttons or whatever they are called are not supported.  Someone started looking at that about a year ago and said it didn't look too hard but then never reported back.

You could try contacting Nikolai Kondrashov and see what he has to say.

Also on the linuxwacom-devel mail list they are in the process of adding support for HP TC1100 buttons right now.  You might want to add a feature request or inquire on the linuxwacom-discuss list:  [http://sourceforge.net/projects/linuxwacom/](http://sourceforge.net/projects/linuxwacom/)

Good luck!

---

### Post by LordOfDragons on 2011-07-12
Let's see if we get there anywhere. Support for hot-buttons on tablets is just a must as it makes working easier without having to hunt for UI elements.

---

### Post by Favux on 2011-07-12
I beg your pardon.  I just noticed looking at your *xinput list-props* I see you have your Waltop tablet on the evdev X driver and not the wacom X driver.  We should probably fix that.

What is the output of *xinput list*?  What does your .conf file that matches the Waltop to the Wacom driver look like and where is it?

---

### Post by LordOfDragons on 2011-07-12
> **Favux said:**
> I beg your pardon.  I just noticed looking at your *xinput list-props* I see you have your Waltop tablet on the evdev X driver and not the wacom X driver.  We should probably fix that.

What is the output of *xinput list*?  What does your .conf file that matches the Waltop to the Wacom driver look like and where is it?
```
roland@dragtop:~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=12   [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet   id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                            id=9    [slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons                 id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]
    &#8627; WALTOP International Corp. Media Tablet   id=13   [slave  keyboard (3)]
    &#8627; WALTOP International Corp. Media Tablet   id=14   [slave  keyboard (3)]
```

What .conf file do you mean?

---

### Post by Favux on 2011-07-12
The xinput list doesn't look correct.  You shouldn't have the Waltop showing up in the keyboard section, it should only be in pointer.

Did you edit the 50-wacom.conf in /usr/share/X11/xorg.conf.d?  Or did you create a 52-waltop-on-wacom.conf in /etc/X11/xorg.conf.d?

---

### Post by LordOfDragons on 2011-07-12
> **Favux said:**
> The xinput list doesn't look correct.  You shouldn't have the Waltop showing up in the keyboard section, it should only be in pointer.

Did you edit the 50-wacom.conf in /usr/share/X11/xorg.conf.d?  Or did you create a 52-waltop-on-wacom.conf in /etc/X11/xorg.conf.d?
Nope, as I read this should be no more required in Natty.

---

### Post by Favux on 2011-07-12
You have a mistaken impression.  The 50-wacom.conf in Natty does not include WALTOP in the match line.  That is why I suggest you add the match with the 52-waltop-on-wacom.conf.  The match will be there and automatic on Oneiric, most likely.

---

### Post by LordOfDragons on 2011-07-12
> **Favux said:**
> You have a mistaken impression.  The 50-wacom.conf in Natty does not include WALTOP in the match line.  That is why I suggest you add the match with the 52-waltop-on-wacom.conf.  The match will be there and automatic on Oneiric, most likely.
and how does this file look like?

---

### Post by Favux on 2011-07-12
Hmm.  We are mis-communicating.

I'm talking about the HOW TO on the first page of this thread in the first post.  There is an example .conf there in the Natty and Maverick part.  Are you asking something else?

---

### Post by LordOfDragons on 2011-07-13
Didn't see it's for Natty. That said it says it needs a patched kernel. Does it then even work with the stock kernel?

---

### Post by LordOfDragons on 2011-07-14
Now it looks like this:
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=12   [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet stylus    id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                            id=9    [slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons                 id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]
```Still though no reactions from buttons:
```
xinput --list-props "WALTOP International Corp. Media Tablet stylus"
Device 'WALTOP International Corp. Media Tablet stylus':
        Device Enabled (121):   1
        Coordinate Transformation Matrix (123): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (240):     0
        Device Accel Constant Deceleration (241):       1.000000
        Device Accel Adaptive Deceleration (242):       1.000000
        Device Accel Velocity Scaling (243):    10.000000
        Wacom Tablet Area (501):        0, 0, 16383, 16383
        Wacom Rotation (502):   0
        Wacom Pressurecurve (503):      0, 0, 100, 100
        Wacom Serial IDs (504): 1280, 0, 2, 0
        Wacom Capacity (505):   -1
        Wacom Pressure Threshold (506): 27
        Wacom Sample and Suppress (507):        2, 4
        Wacom Enable Touch (508):       0
        Wacom Hover Click (509):        0
        Wacom Enable Touch Gesture (510):       0
        Wacom Touch Gesture Parameters (511):   50, 20, 250
        Wacom Tool Type (512):  "STYLUS" (388)
        Wacom Button Actions (513):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Debug Levels (514):       0, 0
```

---

### Post by Favux on 2011-07-14
Good.  You're on the wacom driver now.  Hopefully the stylus behaves better and the stylus side buttons work.

> Still though no reactions from buttons
Right, now you're where I thought you were at when I advised you to post on linuwacom-discuss.

I gather the hot keys don't send key codes.  So running xev and pressing them isn't going to give you anything.

I don't know where the signals are suppose to come from.  I don't know if the Waltop usb kernel driver needs code for the hot keys to produce a signal or not.  Nikolai Kondrashov would seem to be the person to ask and you can check if his DIGImend project site has anything on that.

If there is a signal already there maybe it is coming in with the same protocol packets that send the stylus information?  In which case there is probably a header announcing it is a hot key packet and which hot key it is etc.  You'd have to figure that out.  Again Nikolai Kondrashov is probably the person to ask.

---

### Post by LordOfDragons on 2011-07-14
> **Favux said:**
> Right, now you're where I thought you were at when I advised you to post on linuwacom-discuss.
Done but no reaction. Maybe the mailing list is dead? It's now a couple of days and I got only the email I send there over it.

> I don't know where the signals are suppose to come from.  I don't know if the Waltop usb kernel driver needs code for the hot keys to produce a signal or not.  Nikolai Kondrashov would seem to be the person to ask and you can check if his DIGImend project site has anything on that.
I contacted him but he said he had not much to do with that so he can say nothing at all about it.

> If there is a signal already there maybe it is coming in with the same protocol packets that send the stylus information?  In which case there is probably a header announcing it is a hot key packet and which hot key it is etc.  You'd have to figure that out.  Again Nikolai Kondrashov is probably the person to ask.
As above. He seems to not have been involved. Here the answer he send me:
> I'm sorry, I was only involved with the Linux Wacom driver WRT support for cheap non-Wacom tablets. I never had a Wacom tablet myself, nor was I interested in adding support for any Wacom features..

As far as I remember from the time where I experimented with the aiptek kernel module is that this module (aiptek) sends button presses but the x module did not do anything with it.

---

### Post by Favux on 2011-07-14
It sounds like he didn't understand you have a Waltop tablet and you were asking about the Waltop kernel driver, which he has worked on, transmitting the hot keys.  Instead he thought you were asking about the Wacom X driver xf86-input-wacom.  The reason both your stylus buttons work in Natty is a patch he submitted to the kernel for Waltops.

Well your posting on linuxwacom-discuss showed you weren't on the Wacom X driver.  Maybe that's part of the problem?

> As far as I remember from the time where I experimented with the aiptek kernel module is that this module (aiptek) sends button presses but the x module did not do anything with it. 
That's interesting.  If you could compare the Aiptek source code to the Waltop kernel module source code that might give some clues.  Did the button presses the Aiptek kernel module put through have key codes or what?  To write or adapt xf86-input-wacom code for the hot keys there has to be something from hot key presses being transmitted from the kernel so the Wacom X driver can in turn send them to the X server.  At least that would be my assumption.

---

### Post by xixs on 2012-02-17
> **maslot said:**
> I found a solution for strange behaviour of WALTOP tablet with ID 172f:0037 (I own Aiptek Hyperpen Mini)
If your tablet works like in this post [http://ubuntuforums.org/showpost.php?p=10209416&postcount=21](http://ubuntuforums.org/showpost.php?p=10209416&postcount=21) you can try my magic.
Find a young virgin and black cat, stand in moonlight and wisper this spell:
```

sudo su
lsusb -v

```I checked it on two computers and it works for me.

Thank you, I picked up one of these things for 10quid and although it worked under windows it behaved very strange under ubuntu.


A "sudo lsusb -v" fixes it. Must push the device into some kind of happy state.

Cheers.

---

### Post by barneyjoseph on 2012-04-02
Hi,

I am trying to follow this [**HOW TO Setup a Wacom Tablet with Multi-Monitors in Maverick and Natty**]("http://ubuntuforums.org/showthread.php?t=1656089") tutorial but I've run into trouble right from the start. I am a newbie to Ubuntu and I have Maverick installed on my computer. I have an iBall PF1209 drawing tablet which I am trying to restrict to one monitor. My input list looks like this.

```

xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=10    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=11    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                      id=8    [slave  keyboard (3)]


```As you may have noticed... there is a funny ascii character next to the tablet's device name. When I try to list out its properties: 

```

xinput --list-props "TabletPF1209 "
unable to find device TabletPF1209

```I cannot get past this stage because of the funny device name that my tablet has. So here is my question: **Can the device name be changed?**

Any help would be greatly appreciated!

Thanks,
Barney.

---

### Post by Favux on 2012-04-02
Hi Barney,

I believe you have a UC-Logic tablet (Vendor ID = 5543).  If you run in a terminal:
```
lsusb
```
you should see 5543:0042 wiht 0042 = Product ID.  I assume you are using the WizardPen driver.

Well you can use the Device ID #, in this example 10 or 11 0r 12, probably 10 for the stylus.
> Can the device name be changed?
You'd have to make the change in the kernel driver for UC-Logic tablets, hid-uclogic.ko (i.e. hid-uclogic.c source code).  Possible, see [HOW TO Add Support for KYE, UC-logic, and Waltop Tablets in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1946486").


You should be able to use the mishappened name.  The leading whitespaces count.  I don't think trailing whitespaces do.  So at a guess the name to use is "                TabletPF1209".  The obvious problem being you have 3 devices exported from the kernel with the same name.  That isn't something I've seen with the WizardPen driver that I can recall.

---

### Post by noran on 2012-05-08
Hello,

I tried everything on Pangolin, but my tablet still isn't picked up. Every now and then it magically moves the mouse cursor for two seconds, but then it stops responding again. I can see it in lsusb and also on the list of wacom devices.

Appreciate any help on this,

Noran

---

### Post by Favux on 2012-05-08
Hi noran,

Let's look at a few things.  What is the output of the following terminal commands?
```
lsusb
```
and
```
xinput list
```
and
```
xsetwacom list
```

---

### Post by noran on 2012-05-09
Hello Favux,

Thanks for the response. Here are the outputs.

**lsusb**
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05ca:1814 Ricoh Co., Ltd HD Webcam
Bus 002 Device 003: ID 1c4f:0003 SiGma Micro HID controller
Bus 002 Device 004: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 005: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 002 Device 006: ID 172f:0037 Waltop International Corp. 
```

**xinput list**
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SIGMACH1P U+P Mouse                     	id=11	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=13	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=14	[slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet     stylus	id=16	[slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet     eraser	id=17	[slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet     pad	id=18	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_3M             	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys         
```

[B]xsetwacom list
[/B]
```
         WALTOP             Tablet     stylus	id: 16	type: STYLUS    
         WALTOP             Tablet     eraser	id: 17	type: ERASER    
         WALTOP             Tablet     pad	id: 18	type: PAD    
```

---

### Post by noran on 2012-05-09
Also, the tablet works perfectly on Windows :)

---

### Post by Favux on 2012-05-09
The Product ID 0037 from *ID 172f:0037* in the **lsusb** indicates you have what's called the Waltop Q Pad on the DIGImend site.  I believe the kernel support for that starts with the 3.3 kernel which is why it isn't working on Precise's 3.2 kernel.  If so you will need to either apply the kernel-patches-5 or use one of the pre-compiled DIGImend kernels.

SourceForge has been down all day so I can't confirm things and you can't get the kernel yet.  More details on this and instructions for patching are on this HOW TO:  [http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)

Hopefully SourceForge will be up tomorrow and you can get sorted out.

---

### Post by Favux on 2012-05-09
Hurrah!  SourceForge has mediawiki up and running.  I was wrong your tablet will be supported in the 3.4 kernel.  But I was right in that you either need a kernel or the patches:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

Kernel package instructions:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_packages](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_packages)

Kernel packages:  [http://sourceforge.net/projects/digimend/files/kernel-packages/kernel-patches-5/](http://sourceforge.net/projects/digimend/files/kernel-packages/kernel-patches-5/)

The patch and instructions are on the HOW TO linked above.

---

### Post by noran on 2012-05-10
Hello Favux,

Thank you very much :). I opened the links you gave me, downloaded some of the things there, but I have to say I'm completely clueless and can't find the instructions. On which page exactly are they?

Noran

---

### Post by Favux on 2012-05-10
There's some more instructions on the blog but WordPress is still down at SourceForge.  It's should be in the links above and also in the link to the HOW TO I gave you in post #62.  You might want to skim through some of the introductory information there.

If you want a kernel you use the one closest to the one you have and run it's deb and it will install.  You also want to install its corresponding image deb.  It usually means you're running on a slightly older kernel than the current one, say something like 3.2.32 instead of 3.2.37 or whatever.  Then when you boot up you select the kernel that has the tablet support.

Remember to upgrade grub2 so you can see the kernel after you install it.  Don't think the Debian package manager handles that.  In a terminal:
```
sudo update-grub
```

By the way what release of Ubuntu are you using?  Precise?


If this still isn't clear we can work on adding to the instructions on the HOW TO until you understand them.  Then if needed I can modify the DIGI*mend* wiki.

---

### Post by artspace on 2012-11-01
It's me again... I've just upgraded to Ubuntu 12.04.1 via a clean installation but I just cannot get my tablet to work... The cursor always stick at the top left corner and never move.

I've followed Favux's instruction and I got problem from the first step: I found there was no xf86-input-wacom installed in my newly installed Pangolin. I couldn't find it in the Synaptic Package Manager either, even I added the Doctormo's repositories.

So I tried to ignore the xf86 stuff and created the /etc/X11/xorg.conf.d/52-waltop-on-wacom.conf file, and this didn't help at all even rebooted many times.

My tablet is a Waltop based tablet/screen digitizer (branded ACCU) and I used it smoothly under Ubuntu 10.04LTS (Thank you Favux!), but everything went wrong after upgrading....

the lsusb shows:
```
Bus 004 Device 003: ID 172f:0051 Waltop International Corp. 
```

the xinput list shows:
```
&#9116;   &#8627; WALTOP International Corp. PEN-INPUT DEVICE stylus	id=12	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. PEN-INPUT DEVICE eraser	id=13	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. PEN-INPUT DEVICE pad	id=14	[slave  pointer  (2)]

```

cat /proc/bus/input/devices:
```
I: Bus=0003 Vendor=172f Product=0051 Version=0110
N: Name="WALTOP International Corp. PEN-INPUT DEVICE"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input10
U: Uniq=
H: Handlers=mouse1 event10 
B: PROP=0
B: EV=1b
B: KEY=c03 70001 0 0 0 0
B: ABS=100000f
B: MSC=10

```

and the 50-wacom.conf:
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
	Identifier "Waltop class"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection

```

Any help is greatly appreciated!! Thanks!!

---

### Post by Favux on 2012-11-01
Hi artspace,

> My tablet is a Waltop based tablet/screen digitizer (branded ACCU) and I used it smoothly under Ubuntu 10.04LTS (Thank you Favux!), but everything went wrong after upgrading....
I assume in Lucid you were using the WizardPen driver, correct?  Using this Waltop HOW TO?

I don't see the PID (product ID) = 0051 on the Supported Tablet page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)  It appears your model is not yet supported in the kernel.  Which likely means the DIGImend needs diagnostics on your tablet in order to add kernel driver support.  Instructions on how to do that are available here:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics)  Both of the above links are from the DIGImend main page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)

The **xinput list** indicates you have the tablet on the Wacom X driver because you are seeing stylus, eraser, and pad appended to the parent device name "WALTOP International Corp. PEN-INPUT DEVICE".  Running **xsetwacom list** would confirm that.  The pointer in the top left corner, which is the origin (0,0), indicates the X Server is not getting coordinates from the Wacom X driver.  Indicating the kernel driver is not yet "correct" for the Wacom X driver to handle.

While you are waiting for Nick to fix the kernel driver we may be able to get the tablet working with the WizardPen driver.  We just recently got it to compile in Precise:  [http://ubuntuforums.org/showpost.php?p=12307583&postcount=27](http://ubuntuforums.org/showpost.php?p=12307583&postcount=27)  I strongly suspect we'll need to make a custom .conf file in order for the tablet to work.

---

### Post by artspace on 2012-11-01
Thank you so much Favux!!!AGAIN!!! It works now after installing the wizardpen driver! I actually found several instructions about how to install wizardpen driver on Precise before coming here, but nothing worked. Your instruction is so clear and easy to follow and is so much better then other "how to" I found.

Now I only have some calibration problem which I met before in Lucid and I think I can fix it when I come back from work later.

Thanks Favux!!!

---

### Post by Favux on 2012-11-01
You're welcome.  Nice job!  :)

Could you tell me if **./configure --prefix=/usr** worked or did you need to use **./autogen.sh --prefix=/usr**?

Also when you get the .conf file working would you mind posting it?

---

### Post by artspace on 2012-11-02
> **Favux said:**
> You're welcome.  Nice job!  :)

Could you tell me if **./configure --prefix=/usr** worked or did you need to use **./autogen.sh --prefix=/usr**?

Also when you get the .conf file working would you mind posting it?
I used ./autogen.sh --prefix=/usr

And my 52-waltop.conf is:
```
Section "InputClass"
	Identifier "Waltop pen"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
#	Driver "wacom"
	Driver "wizardpen"
        # Apply custom Options below.
	Option		"TopZ"		"50"  # pressure threshold
	Option		"TopX"		"-10"
	Option		"TopY"		"-10"
	Option		"BottomX"	"7210"
	Option		"BottomY"	"5410"
EndSection
```

The option settings are same as the Lucid version. :-D

---

### Post by Favux on 2012-11-02
Thanks artspace.  Sweet.

It looks like make clean doesn't have anything to do with getting configure to work and the autogen line is what is needed.  I suppose I should investigate that some more.  But if we have something that works I sure appreciate avoiding having to look into all the Makefile build stuff. ;)

And its nice the .conf is the same.  Sort of expected that but good to have it confirmed.

Also I forgot to ask.  Just to confirm, is pressure working?  And do the pen buttons work?

---

### Post by artspace on 2012-11-02
> **Favux said:**
> Also I forgot to ask.  Just to confirm, is pressure working?  And do the pen buttons work?
Yes! They are both working perfectly!:biggrin:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=226574&stc=1&d=1351866291[/IMG]

---

### Post by Favux on 2012-11-02
Nice!  :)

---

### Post by cawilliams1983 on 2013-01-24
Hey, Favux!

I need help from where Nolan left off.  I have the same tablet as his, the Waltop Q, and can see that it isn't supported by my current kernal which is 3.2.0-36.  I'm not sure which package I should download from sourceforge?

As a side, with these Q pads, the name of the device is MADDENING.  I kept trying to list the parameters of the stylus with xsetwacom and kept putting "stylus" and getting back that "stylus" isn't a device...  we you have to put in "         WALTOP             Tablet     stylus" spaces and all..  Just wanted to post that in case anyone else is pulling their hair out knowing good and well that it says "stylus."

Edit:

The spaces and caps were taken from my device name quoted above..  just copy the device name exactly as it's listen in xsetwacom --list devices...  no matter how awkward it is..

---

### Post by cawilliams1983 on 2013-01-24
Okay, I went back and looked at version 6 patches (I was looking at 5 before) but didn't see my kernal.  Has it not been DIGImended yet?  If not, is there anything else I can do?

---

### Post by Favux on 2013-01-25
Hi cawilliams1983,

It's in the version 6 patches, so you can use those on the 3.2 or Precise kernel and patch and compile the modules you need.  If you want to use a pre-rolled kernel you'd have to use linux_3.2.0-31.50 which is the closest to your current 3.2.0-36.

---

### Post by cawilliams1983 on 2013-01-25
hmm..  which one of those options would you recommend, the pre-rolled or patch?  I don't really understand the system implications of either.

---

### Post by floric on 2013-01-29
Hey,
at first, thanks for this great support for low-budged-tablets. :)
I might buy a branded version of the **Waltop Mars A**-tablet:
[http://www.waltop.com/english/01_products/02_detail.php?SID=146](http://www.waltop.com/english/01_products/02_detail.php?SID=146)
So I took a look at your support-list and for other linux drivers.
Unfortunately there weren't any discussions or texts about this tablet. So it seems to be quite new on the market.
Do you think, there will work drivers for other, similar tablets or do you know it with another name?
I would buy the branded version from Medion (MEDION P82018 (MD 86635)). Thats a german company but the tablet seems to be the one by Waltop based on the picture and the specifications.
Regards, Flo

---

### Post by Favux on 2013-01-29
Hi floric,

Welcome to Ubuntu forums!


Fabian reported in December 2012.
> I just tried out my new graphics tablet and as it seems, it's not fully
supported.
The two buttons both trigger the same response.
And I have no idea how to use the 8 pseudo-buttons (called "macro keys"
on the Waltop site)

Everything else seems to work ok (full area, pressure sensitivity).

Details:
Name: "Medion P82018 (MD 86635)"
identifier: "ID 172f:0047 Waltop International Corp."

registers (in /var/log/syslog) as:
input: WALTOP International Corp. Mars Tablet as
/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input26
generic-usb 0003:172F:0047.000C: input,hidraw1: USB HID v1.10 Mouse
[WALTOP International Corp. Mars Tablet] on usb-0000:00:04.0-5/input0

Official Waltop product (I guess):
Waltop Mars A
[http://www.waltop.com/english/01_products/02_detail.php?SID=146](http://www.waltop.com/english/01_products/02_detail.php?SID=146)

Features:
- 2048 pressure steps
- 4000 lpi precision
Nick also mentioned the Mars on another topic we were discussing.  So the project knows about this new Waltop.  Even though it isn't on the Tablet Support Status page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

Because Nick took a new job a few months ago things have slowed down a lot.  He is looking for developers to help on the DIGI*mend* project.  Looks to me like at least 3 core developers would be good.  So it may be a while before a fixed kernel driver that addresses the button issue and whatever for the Mars is ready to be tested and submitted to the kernel.  Not even sure the diagnostics have been submitted for the Mars:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  If not and you get the tablet maybe you'd like to?

---

### Post by floric on 2013-01-29
Hey,
thanks for your answer.
I have some years of simple linux experience, want to use the tablet for GIMP, (maybe Krita) and mostly for Blender. BTW I began to study computer sciences (specialized on media). So I'm also learning coding and related stuff at university. ;)
So if I can count on your help, I'll help you, buy it and will give you log messages and so on. :)
Very likely I'll buy it on thursday if I can get one.
Regards, Flo

---

### Post by floric on 2013-01-30
Btw, here is an response to my mail asking for linux drivers:
> Hello, Mr.... ,

We don’t have supporting drivers on Linux OS for our tablets.

But there are several models which Linux built-in driver can support.
*

A model similar to Mars A and can work on Linux is “Slim 12.1”, which should work on Linux 11 above.

You may find the product spec from below link.

[http://www.waltop.com/english/01_products/01_list.php?MID=29](http://www.waltop.com/english/01_products/01_list.php?MID=29)
*

Thanks.

Sharon

---

### Post by Favux on 2013-01-30
Once upon a time they did have a driver based on linuxwacom.  But now that I check my download link it is a **Not Found**.  It took forever to figure out how to get it to build:  [http://ubuntuforums.org/showthread.php?t=1326789](http://ubuntuforums.org/showthread.php?t=1326789)  And then when we finally got it compiled it turned out not to work.

But xf86-input-wacom incorporated the Waltop tablet ID table from it when it added Waltop support.

That was one of the reasons behind the WizardPen driver project I guess.  Get a driver to support UC_LOGIC, Waltop, and some other tablets.  Nick participated in that early on.  But there was some disagreement on direction apparently.  Eventually the other dev.s abandoned WizardPen development.

So now Nick fixes the usb HID descriptors (the kernel drivers) and once that's done the Waltops work fine with the Pen on the xf86-input-wacom (xorg-xserver-input-wacom) X driver and the buttons on the evdev X driver.

---

### Post by floric on 2013-01-31
Great news. It works out-of-the-box using Ubuntu 12.04. :)
I tried it in GIMP and Blender, both recognizing pressure and direction perfectly.
BTW lsusb shows the tablet as:
>  Waltop International Corp. 
Now: painting. :)

---

### Post by Favux on 2013-01-31
Good!  :)


Also important from **lsusb** is the Vendor ID and Product ID, which would be something like 172F:05**.  That uniquely identifies the tablet.

---

### Post by floric on 2013-01-31
lsusb
> Bus 008 Device 002: ID 172f:0047 Waltop International Corp. 
If you need more information to improve the drivers, just ask.

---

### Post by yusuke494 on 2013-02-01
Hi

I'm developping Waltop tablet driver which supports "tablet mode".
My Page:[http://yusuke494.web.fc2.com/english/](http://yusuke494.web.fc2.com/english/)

How did Xorg wacom driver detect Mars A tablet?

Probably the following line exists in /var/log/Xorg.0.log.

(--) WALTOP **** stylus: Wacom USB **** tablet maxX=**** maxY=**** maxZ=**** resX=**** resY=**** tilt=****

Please tell me about these values in this line.

---

### Post by floric on 2013-02-02
Hey,
here is the relevant part of the Xorg-file:
> florian@florian-desktop:~$ cat /var/log/Xorg.0.log | grep WALTOP
[     4.719] (II) config/udev: Adding input device WALTOP International Corp. Graphics Tablet (/dev/input/event9)
[     4.719] (**) WALTOP International Corp. Graphics Tablet: Applying InputClass "evdev pointer catchall"
[     4.719] (**) WALTOP International Corp. Graphics Tablet: Applying InputClass "evdev keyboard catchall"
[     4.719] (**) WALTOP International Corp. Graphics Tablet: Applying InputClass "evdev tablet catchall"
[     4.719] (**) WALTOP International Corp. Graphics Tablet: Applying InputClass "Waltop class"
[     4.755] (II) Using input driver 'wacom' for 'WALTOP International Corp. Graphics Tablet'
[     4.755] (**) WALTOP International Corp. Graphics Tablet: always reports core events
[     4.759] (II) WALTOP International Corp. Graphics Tablet: type not specified, assuming 'stylus'.
[     4.759] (II) WALTOP International Corp. Graphics Tablet: other types will be automatically added.
[     4.759] (--) WALTOP International Corp. Graphics Tablet stylus: using pressure threshold of 27 for button 1
[     4.759] (--) WALTOP International Corp. Graphics Tablet stylus: Wacom Unknown USB tablet maxX=20000 maxY=12500 maxZ=2047 resX=1016 resY=1016  tilt=enabled
[     4.759] (II) WALTOP International Corp. Graphics Tablet stylus: hotplugging dependent devices.
[     4.759] (EE) WALTOP International Corp. Graphics Tablet stylus: Invalid type 'cursor' for this device.
[     4.759] (EE) WALTOP International Corp. Graphics Tablet stylus: Invalid type 'touch' for this device.
[     4.759] (II) WALTOP International Corp. Graphics Tablet stylus: hotplugging completed.
[     4.808] (II) XINPUT: Adding extended input device "WALTOP International Corp. Graphics Tablet stylus" (type: STYLUS, id 8)
[     4.808] (**) WALTOP International Corp. Graphics Tablet stylus: (accel) keeping acceleration scheme 1
[     4.808] (**) WALTOP International Corp. Graphics Tablet stylus: (accel) acceleration profile 0
[     4.808] (**) WALTOP International Corp. Graphics Tablet stylus: (accel) acceleration factor: 2.000
[     4.808] (**) WALTOP International Corp. Graphics Tablet stylus: (accel) acceleration threshold: 4
[     4.808] (II) config/udev: Adding input device WALTOP International Corp. Graphics Tablet (/dev/input/mouse0)
[     4.816] (**) WALTOP International Corp. Graphics Tablet eraser: Applying InputClass "evdev pointer catchall"
[     4.816] (**) WALTOP International Corp. Graphics Tablet eraser: Applying InputClass "evdev keyboard catchall"
[     4.816] (**) WALTOP International Corp. Graphics Tablet eraser: Applying InputClass "evdev tablet catchall"
[     4.816] (**) WALTOP International Corp. Graphics Tablet eraser: Applying InputClass "Waltop class"
[     4.816] (II) Using input driver 'wacom' for 'WALTOP International Corp. Graphics Tablet eraser'
[     4.816] (**) WALTOP International Corp. Graphics Tablet eraser: always reports core events
[     4.816] (--) WALTOP International Corp. Graphics Tablet eraser: Wacom Unknown USB tablet maxX=20000 maxY=12500 maxZ=2047 resX=1016 resY=1016  tilt=enabled
[     4.832] (II) XINPUT: Adding extended input device "WALTOP International Corp. Graphics Tablet eraser" (type: ERASER, id 13)
[     4.832] (**) WALTOP International Corp. Graphics Tablet eraser: (accel) keeping acceleration scheme 1
[     4.832] (**) WALTOP International Corp. Graphics Tablet eraser: (accel) acceleration profile 0
[     4.832] (**) WALTOP International Corp. Graphics Tablet eraser: (accel) acceleration factor: 2.000
[     4.832] (**) WALTOP International Corp. Graphics Tablet eraser: (accel) acceleration threshold: 4
[     4.832] (**) WALTOP International Corp. Graphics Tablet pad: Applying InputClass "evdev pointer catchall"
[     4.832] (**) WALTOP International Corp. Graphics Tablet pad: Applying InputClass "evdev keyboard catchall"
[     4.832] (**) WALTOP International Corp. Graphics Tablet pad: Applying InputClass "evdev tablet catchall"
[     4.832] (**) WALTOP International Corp. Graphics Tablet pad: Applying InputClass "Waltop class"
[     4.832] (II) Using input driver 'wacom' for 'WALTOP International Corp. Graphics Tablet pad'
[     4.832] (**) WALTOP International Corp. Graphics Tablet pad: always reports core events
[     4.832] (--) WALTOP International Corp. Graphics Tablet pad: Wacom Unknown USB tablet maxX=20000 maxY=12500 maxZ=2047 resX=1016 resY=1016  tilt=enabled
[     4.848] (II) XINPUT: Adding extended input device "WALTOP International Corp. Graphics Tablet pad" (type: PAD, id 14)
[     4.848] (**) WALTOP International Corp. Graphics Tablet pad: (accel) keeping acceleration scheme 1
[     4.848] (**) WALTOP International Corp. Graphics Tablet pad: (accel) acceleration profile 0
[     4.848] (**) WALTOP International Corp. Graphics Tablet pad: (accel) acceleration factor: 2.000
[     4.848] (**) WALTOP International Corp. Graphics Tablet pad: (accel) acceleration threshold: 4


EDIT: Whats the advantage of your driver?
Is the tablet mode the mode which always uses the fullscreen based on the monitor? I can only activade this in the wacom-settings.

---

### Post by yusuke494 on 2013-02-02
Thank you, floric

According to your Xorg-file, your tablet is running with maxX=20000, maxY=12500.

Your tablet resolution is 4000 LPI(lines per inch) at 10" x 6.25", thus maxX and maxY should be as follows. 

maxX = 4000 LPI x 10" = 40000 lines
maxY = 4000 LPI x 6.25" = 25000 lines

Waltop tablets have some running modes.

Default mode: restricted tablet resolution
Tablet mode: native tablet resolution

I guess your tablet is running with 2000 LPI in "Default mode".

My driver enables Waltop tablet to run in "Tablet mode", but hasn't support Mars A yet.

---

### Post by floric on 2013-02-02
Ah, makes sense. I'll try it, if your driver is ready.

---

