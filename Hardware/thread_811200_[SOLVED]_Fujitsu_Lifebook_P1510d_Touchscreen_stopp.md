---
title: "[SOLVED] Fujitsu Lifebook P1510d Touchscreen stopped working in Hardy"
date: 2008-05-28
forum: Hardware
---

### Post by CMEPTb on 2008-05-28
Hey guys,

As title indicates, Fujitsu touchscreen stopped working for me with the new X that comes with Hardy. I managed to make it work with gutsy using guide at [http://www.conan.de/touchscreen/]("http://www.conan.de/touchscreen/"), but with the recent update, I get this when I grep "(EE)" in my /var/log/Xorg.0.log:


> (EE) module ABI major version (0) doesn't match the server's version (2)
(EE) Failed to load module "fujitsu" (module requirement mismatch, 0)
(EE) Failed to load module "void" (module does not exist, 0)
(EE) No Input driver matching `fujitsu'
(EE) No Input driver matching `void'

Here is my xorg.conf:

> 
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
#	Uncomment to use MIddle Click + Mouse for scroll
#	Option "EmulateWheel" "true" 
#	Option "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	Option 		"RandRRotation" "True"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice 	"touchscreen" "CorePointer"
	InputDevice 	"dummy"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
#	InputDevice	"Synaptics Touchpad"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "146"
    Option "MaxX" "4036"
    Option "MaxY" "3999"
    Option "SendCoreEvents" "On"
EndSection


I would very much like to fix this, but I just don't have an idea how to do this. Can anyone give some insights?


Also, if I'll fail to fix this, is there an easy re-roll method to Gutsy, or I'll be stuck with reinstalling the whole system with all soft and customizations I did?

Thanks for you time and advice.

---

### Post by CMEPTb on 2008-06-05
Shameless bump.

Anyone got any ideas?

---

### Post by danmiddle2 on 2008-06-12
> **CMEPTb said:**
> Shameless bump.

Anyone got any ideas?

I have a P1510 with the same problem. The problem is that the driver is not compatible with the new version of Xorg that comes with Hardy. You need to compile from source and this may fix the problem... but I haven't got time. 

I am just going to keep an eye on conan.de for a new version and sort it then.

Sorry that its not of much help

Dan

---

### Post by concertedrxn on 2008-06-13
**UPDATE:**  The script below does not work for Jaunty or any later version of Ubuntu.  Please follow the instructions given in [message #37]("http://ubuntuforums.org/showpost.php?p=7180185&postcount=37") of this thread.


I have the Fujitsu P-Series driver working on my P1510D under Hardy. I wrote a script to automate the download, compilation, and installation of the driver (see below).  First you need to open a Terminal window by clicking on the Applications menu, going to Accessories and selecting Terminal.  In the Terminal window type the following on the command line to launch the gedit text editor:

```
gedit touchscreen.sh
```

Next, copy the script code below and paste it into the gedit window.  Click the "Save" button and close gedit.

```
#!/bin/bash

# Change to /tmp to avoid cluttering the current directory.
cd /tmp

# Install the packages we need for setting up the serial port and compiling the driver's source code.
sudo apt-get install -y setserial xserver-xorg-dev x11proto-core-dev x11proto-fonts-dev build-essential pkg-config libxrandr-dev

# Configure the serial port to which the touchscreen is attached.
sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfig

# Set it up so that the serial port will be properly configured at boot time.
echo -e '/dev/ttyS0 irq 4 port 0x220 autoconfig' | sudo tee /etc/serial.conf

# Download the driver's source code from the web site.
wget http://www.conan.de/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2

# Extract the source code from the file.
tar -jxf xf86-input-fujitouch-0.6.5.tar.bz2

# Change to the source code subdirectory.
cd xf86-input-fujitouch-0.6.5

# Back up the source code file that we need to edit.
cp fujitsu.c fujitsu.c.original

# Patch the source code to allow the driver to work in Hardy.
sed	'
	s:xf86AlwaysCore(local, TRUE);:/*xf86AlwaysCore(local, TRUE);*/:
	' fujitsu.c.original >fujitsu.c

# Compile the source code and install the driver. 
./configure --prefix=/usr && make && sudo make install

exit 0
```

Now type the following into the Terminal:

```
sh touchscreen.sh
```

Hit enter, enter your password, and watch the script do its work.
:popcorn:

After executing the script, you'll need to modify your xorg.conf file manually. First, backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Next, open your xorg.conf file for editing:

```
sudo gedit /etc/X11/xorg.conf
```

Add the following to the xorg.conf file somewhere near the other "InputDevice" entries:

```
Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "146"
    Option "MaxX" "4036"
    Option "MaxY" "3999"
    Option "SendCoreEvents" "On"
EndSection
```

(On my P1510D, I have 4020 for MaxX rather than 4036.)

Then find the "ServerLayout" section of the xorg.conf file and add the following to that section:

```
InputDevice "touchscreen"
```

Once you have finished making the changes, click "Save" and close gedit.

Now logout of the X session.  When the GDM login screen appears, you should be able to move the cursor using the touchscreen.

I hope this helps!

---

### Post by danmiddle2 on 2008-06-14
Thanks - that worked for me.

I had to install the following packages first, though:
sudo apt-get install xserver-xorg-dev x11proto-core-dev x11proto-fonts-dev

---

### Post by concertedrxn on 2008-06-14
danmiddle2,

Thanks for catching that.  I've included your fix in the script so others won't encounter that problem.  I apologize for the oversight.

---

### Post by CMEPTb on 2008-06-14
Many thanks concertedrxn, worked like a charm.

You're the best!

---

### Post by djrakun on 2008-06-15
Hi guys, 

I'm trying this on a fujitsu lifebook T4010D.  I must not have C configured correctly because when I run your script an error is returned that says 
"configure: error: C compiler cannot create executables".  Am I missing a component that I should get using apt?

Another note:  The error tells me to check the config.log for more details.  I was going to post the contents of this log however when I try to locate a file called config.log, the only thing that returns is "/var/log/fontconfig.log"

thanks in advance for your help!

---

### Post by danmiddle2 on 2008-06-16
have you installed all the build tools

sudo apt-get install build-essential

---

### Post by danmiddle2 on 2008-06-16
> **djrakun said:**
> Hi guys, 

I'm trying this on a fujitsu lifebook T4010D. 

Does that have the same touchscreen hardware?... I think this driver is just for the fujitsu P series!? have a look at [www.conan.de](www.conan.de)

---

### Post by concertedrxn on 2008-06-16
djrakun,

Did you try danmiddle2's suggestion to install build-essential?  If so, did that solve your problem?  I went ahead and added it to the script since it won't cause any harm, but I would like to know for certain that it was what you needed.

---

### Post by dew7777 on 2008-06-17
I just installed xubuntu on a fujitsu p1120 and the touchscreen worked before I installed the script and it still does but my problem is how do i calibrate the touchscreen.  When I touch the screen the arrow moves like 4 inches away.

---

### Post by CMEPTb on 2008-06-18
> **dew7777 said:**
> I just installed xubuntu on a fujitsu p1120 and the touchscreen worked before I installed the script and it still does but my problem is how do i calibrate the touchscreen.  When I touch the screen the arrow moves like 4 inches away.

It most surely has something to do with MIN and MAX values in the code you add to xorg.conf:

```

Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "146"
    Option "MaxX" "4036"
    Option "MaxY" "3999"
    Option "SendCoreEvents" "On"
EndSection
```

Not sure what those values actually are, I guess it has something to do with your screen. My resolution is 1024x600 and I see not much pattern there. I hope someone will clear that out for ya.

EDIT: Try googling the correct values for your model number, it should be the same for any X version, and I'm quite sure someone had troubles getting it to work in the past.

---

### Post by danmiddle2 on 2008-06-18
> **dew7777 said:**
> I just installed xubuntu on a fujitsu p1120 and the touchscreen worked before I installed the script and it still does but my problem is how do i calibrate the touchscreen.  When I touch the screen the arrow moves like 4 inches away.

This site seems to have what you are after
[http://ariescomputing.com/lifebook/](http://ariescomputing.com/lifebook/)

---

### Post by Bruce McGoose on 2008-06-25
Had to register on here to say thanks :)
Saved hours / days of my time


The script failed halfway through, needed to install pkg-config.
Afterwards it worked fine :)

---

### Post by bikenerd on 2008-07-01
The touchscreen.sh script worked a treat, but I´m trying to rotate the screen on my Fujitsu P1510 running Ubuntu Hardy Heron. 

The command ¨xrandr -o right¨ and Brad Midgeley´s ([http://www.xmission.com/~bmidgley/p1510/](http://www.xmission.com/~bmidgley/p1510/)) rotate.sh script successful rotates the screen, but the mouse and stylus behave crazy (movements of the mouse or stylus in an X direction are translated into cursor movements in a Y direction).

A bit of web research ([http://popey.com/A_GUI_for_RandR_and_xsetwacom](http://popey.com/A_GUI_for_RandR_and_xsetwacom)) suggests the command:
sudo xsetwacom set touchscreen Rotate cw

should fix the problem.  Running the command doesn´t return an error message but it doesn´t correct the crazy mouse movement.

(I called the device ¨touchscreen¨ because that´s the Device Name in xorg.conf - and because names like cursor and stylus return error messages like

Set: Failed to open device 'stylus'


Has anyone else attempted to use the touchscreen.sh under hardy heron and rotate the screen?

---

### Post by danmiddle2 on 2008-07-01
> **bikenerd said:**
> The touchscreen.sh script worked a treat, but I´m trying to rotate the screen on my Fujitsu P1510 running Ubuntu Hardy Heron. 

The command ¨xrandr -o right¨ and Brad Midgeley´s ([http://www.xmission.com/~bmidgley/p1510/](http://www.xmission.com/~bmidgley/p1510/)) rotate.sh script successful rotates the screen, but the mouse and stylus behave crazy (movements of the mouse or stylus in an X direction are translated into cursor movements in a Y direction).

A bit of web research ([http://popey.com/A_GUI_for_RandR_and_xsetwacom](http://popey.com/A_GUI_for_RandR_and_xsetwacom)) suggests the command:
sudo xsetwacom set touchscreen Rotate cw

should fix the problem.  Running the command doesn´t return an error message but it doesn´t correct the crazy mouse movement.

(I called the device ¨touchscreen¨ because that´s the Device Name in xorg.conf - and because names like cursor and stylus return error messages like

Set: Failed to open device 'stylus'


Has anyone else attempted to use the touchscreen.sh under hardy heron and rotate the screen?

Rotate doesn't work if you are running compiz desktop effects. To see if this is your issue, try disabling compiz and then using the xrandr rotate command. This works fine for me.

You could even write a script that disables compiz, rotates the screen and re-enables compiz. I started working on this but could not find a compiz-disable command line option.

---

### Post by ukripper on 2008-07-01
> **concertedrxn said:**
> I have the Fujitsu P-Series driver working on my P1510D under Hardy. I wrote a script to automate the download, compilation, and installation of the driver (see below).  First you need to open a Terminal window by clicking on the Applications menu, going to Accessories and selecting Terminal.  In the Terminal window type the following on the command line to launch the gedit text editor:

```
gedit touchscreen.sh
```

Next, copy the script code below and paste it into the gedit window.  Click the "Save" button and close gedit.

```
#!/bin/bash

# Change to /tmp to avoid cluttering the current directory.
cd /tmp

# Install the packages we need for setting up the serial port and compiling the driver's source code.
sudo apt-get install -y setserial xserver-xorg-dev x11proto-core-dev x11proto-fonts-dev build-essential

# Configure the serial port to which the touchscreen is attached.
sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfig

# Set it up so that the serial port will be properly configured at boot time.
echo -e '/dev/ttyS0 irq 4 port 0x220 autoconfig' | sudo tee /etc/serial.conf

# Download the driver's source code from the web site.
wget http://www.conan.de/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2

# Extract the source code from the file.
tar -jxf xf86-input-fujitouch-0.6.5.tar.bz2

# Change to the source code subdirectory.
cd xf86-input-fujitouch-0.6.5

# Back up the source code file that we need to edit.
cp fujitsu.c fujitsu.c.original

# Patch the source code to allow the driver to work in Hardy.
sed	'
	s:xf86AlwaysCore(local, TRUE);:/*xf86AlwaysCore(local, TRUE);*/:
	' fujitsu.c.original >fujitsu.c

# Compile the source code and install the driver. 
./configure --prefix=/usr && make && sudo make install

# Return to the directory where we started.
cd -

exit 0
```

Now type the following into the Terminal:

```
sh touchscreen.sh
```

Hit enter, enter your password, and watch the script do its work.
:popcorn:

After executing the script, you'll need to modify your xorg.conf file manually. First, backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Next, open your xorg.conf file for editing:

```
sudo gedit /etc/X11/xorg.conf
```

Add the following to the xorg.conf file somewhere near the other "InputDevice" entries:

```
Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "146"
    Option "MaxX" "4036"
    Option "MaxY" "3999"
    Option "SendCoreEvents" "On"
EndSection
```

(On my P1510D, I have 4020 for MaxX rather than 4036.)

Then find the "ServerLayout" section of the xorg.conf file and add the following to that section:

```
InputDevice "touchscreen"
```

Once you have finished making the changes, click "Save" and close gedit.

Now logout of the X session.  When the GDM login screen appears, you should be able to move the cursor using the touchscreen.

I hope this helps!

Looks great!! shame i don't have touchscreen. But many people can get help from this. Can you post this Howoto under tutorial section with all this info. People will love this there.

Cheers

---

### Post by concertedrxn on 2008-07-01
bikenerd,

It doesn't rotate for me either, unfortunately.  If you find a solution, let me know.

The command you found is for the wacom driver, so it wouldn't have an effect on this driver.  Looking at the source code, it appears that the ability to rotate with the display is built into the Fujitsu driver, but I don't know how to set rotation without editing the xorg.conf and restarting X.  (More information can be found here: [http://www.conan.de/touchscreen/p-series.html](http://www.conan.de/touchscreen/p-series.html))

---

### Post by concertedrxn on 2008-07-01
ukripper,

I'd be happy to add it to the tutorial section once we know it works as written for everyone with a P1510D.  I'd also like to have the rotation issue figured out.

---

### Post by concertedrxn on 2008-07-02
danmiddle2,

Here's a script I wrote to toggle the rotation of the screen:

```

#!/bin/bash

current=0
compiz=0

xrandr -q | grep 'right (' >/dev/null && current=90
ps -e | grep compiz >/dev/null && touch /tmp/compiz
test -e /tmp/compiz && compiz=1

if [ "$current" -eq 90 ]
	then
#		killall tablet6.en.pl
#		killall onboard
		xrandr --output LVDS --rotate normal

		if [ "$compiz" -eq 1 ]
			then
				compiz --replace &
				rm /tmp/compiz

		fi

 #		~/bin/tablet6.en.pl &

	else
#		killall tablet6.en.pl 
		xrandr --output LVDS --rotate right
		metacity --replace &
#		~/bin/tablet6.en.pl -cw &
#		onboard &

fi

exit=0
```   

The script checks to see if desktop effects are active, disables them for a rotated screen, and re-enables them when toggling back to normal rotation.  If desktop effects aren't enabled, it simply rotates between clockwise and normal orientations.

I used xbindkeys to attach the script to the rotation button on the screen bezel.  I can share the details of that later, if you need them.  I even have xbindkeys working with scripts to use the brightness function keys to control screen brightness.

If you look closely, I've commented out lines that I use to start and kill an on-screen keyboard program called "onboard".  Also, you'll notice a Perl script called "tablet6.en.pl".  That's another "driver" from Sam Engstrom that can be used for the P1510D touch screen and handles screen rotation properly.  More info on that can be found here: [http://samengstrom.com/nxl/3566/p1510_touchscreen_page.en.html]("http://samengstrom.com/nxl/3566/p1510_touchscreen_page.en.html")  If you decide to try the Perl script as your touch screen driver, be sure to comment out the Fujitsu touch screen driver from the "ServerLayout" section in xorg.conf and restart X.

I initially tried Sam Engstrom's driver, had a bear of a time getting the X11:GUITest library compiled (but succeeded after going through dependency hell), and failed to get the script to work.  I tried it again after recently failing to get the Fujitsu driver to rotate properly, and for some reason the Perl script worked.  If I figure out what all I did to get it working, I'll post it here.  The only problem I'm having with it now is getting it to restart automatically after suspending the laptop, which means I have to start it manually if I need it.

---

### Post by labiloute on 2008-07-04
Just to say it works like a charm and to thanks concertedrxn and community for all this great work...
Good job mates long life to open source
:guitar:

---

### Post by danmiddle2 on 2008-07-05
> **concertedrxn said:**
> danmiddle2,

Here's a script I wrote to toggle the rotation of the screen:


Worked like a charm, many thanks!

---

### Post by bikenerd on 2008-07-05
> **danmiddle2 said:**
> Rotate doesn't work if you are running compiz desktop effects. To see if this is your issue, try disabling compiz and then using the xrandr rotate command. This works fine for me.

I removed compiz and compiz-core using synaptic package manager, then ran ¨xrandr -o right¨
No joy .. the mouse is still being all crazy.  


Thanks for the suggestion but it didn´t pay out.

---

### Post by djrakun on 2008-07-20
danmiddle2, sorry I fell off the map for a while.  Installing the build-essentials fixed up my problem, and running the script did enable the touchscreen ( that is I can see the pointer move when my pen gets close to the screen), however I think you are right that either the driver isn't totally compatible or I need to make adjustments in the xorg.conf because my x-y coordinates seem to be off.  If I touch the center of my screen, the pointer is completely off the monitor.  If i move the pen around, I can see the pointer reach the far edges of the screen sometimes.

You got me on my way though.  I'll check out conan.de and see if they have a better driver for my model

---

### Post by djrakun on 2008-07-20
ps concertedrxn, your rotate script works wonderfully with the t4010d.  I've tried several other scripts that couldn't quite pull off the job but yours is spot on.  Now if I could just get the coordinates for my pen control...

---

### Post by djrakun on 2008-07-20
Well, I thought I was being really clever by changing the MaxX and MaxY values to my resolution size but you should never count on passing a test if you're guessing.  
Option "MinX" "0"
Option "MinY" "0"
Option "MaxX" "1024"
Option "MaxY" "768"


I figure it couldn't hurt to include my xorg.conf file here in case anyone can r

ecognize some unneeded garbage that could be causing some trouble


```
# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection


Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "cursor"
        Option          "Mode"          "absolute"
        Option          "Speed"         "3.0"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
#       Option          "MaxX"          "24576"
#       Option          "MaxY"          "18432"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/ttyS0"
        Option          "Type"          "stylus"
        Option          "Mode"          "absolute"
        Option          "Tilt"          "on"
        Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#       Option          "DebugLevel"    "10"
	Option "SendCoreEvents" "true"
EndSection
Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
Option "MinX" "0"
Option "MinY" "0"
Option "MaxX" "1024"
Option "MaxY" "768"
    Option "SendCoreEvents" "On"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/ttyS0"
        Option          "Type"          "eraser"
        Option          "Mode"          "absolute"
        Option          "Tilt"          "on"
        Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
#Option          "DRI"           "false"	
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice "touchscreen"

# Uncomment if you have a wacom tablet
	# TabletPC Pen Device
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by DoItFast4U on 2008-07-25
The scripts and instructions in the thread work amazingly well! Thanks for taking the time to figure out so many details.

I do have one issue though, and I'm wondering if others see the same. If I open an app like Gimp or another drawing program, I don't seem to be able to draw anything. The pointer moves around smoothly, but doesn't seem to register a click when I drag.

I'm currently at these settings trying to fix the problem:

    Option "LongTouchTimer"  "500"
    Option "longtouched_button" "3"
    Option "maybetapped_action" "click"
    Option "maybetapped_button" "1"

Can anyone get their config to allow them to use the stylus to casually draw in a drawing app?

---

### Post by danmiddle2 on 2008-07-25
> **DoItFast4U said:**
> The scripts and instructions in the thread work amazingly well! Thanks for taking the time to figure out so many details.

I do have one issue though, and I'm wondering if others see the same. If I open an app like Gimp or another drawing program, I don't seem to be able to draw anything. The pointer moves around smoothly, but doesn't seem to register a click when I drag.

I'm currently at these settings trying to fix the problem:

    Option "LongTouchTimer"  "500"
    Option "longtouched_button" "3"
    Option "maybetapped_action" "click"
    Option "maybetapped_button" "1"

Can anyone get their config to allow them to use the stylus to casually draw in a drawing app?

works for me, but you have to press harder than perhaps you want to at first.

---

### Post by concertedrxn on 2008-07-25
> **danmiddle2 said:**
> works for me, but you have to press harder than perhaps you want to at first.

The fujitsu driver uses the libtouch library to emulate mouse button actions, and I don't find the way libtouch operates to be very intuitive.  To emulate holding down the left mouse button, you have to press on one spot on the screen for a moment before dragging the stylus. That is what causes difficulty when trying to draw in the GIMP.  It's not that you need more pressure to draw, but by exerting more pressure you probably spend just enough time in one spot to register a left mouse button down event.

---

### Post by deadcyclo on 2008-08-23
Thanks a heap concertedrxn. Your script worked fine on Debian also. But first I had to run sudo apt-get install libxrandr-dev

Edit: Unfortunately after upgrading to lenny it no longer works properly. The touch gets all screwed up after rotating

---

### Post by concertedrxn on 2008-08-29
> **deadcyclo said:**
> Thanks a heap concertedrxn. Your script worked fine on Debian also. But first I had to run sudo apt-get install libxrandr-dev

Edit: Unfortunately after upgrading to lenny it no longer works properly. The touch gets all screwed up after rotating

Thanks for sharing your experience with us.  I've added the package that your system was missing to my script.

Unfortunately, rotation isn't working right in Ubuntu Hardy Heron either.  I'm keeping my eyes open for a solution to the problem, but I haven't seen anything useful yet.  Although I took Pascal classes in college many, many years ago, I'm not a programmer and know very little about C.  We need the author of the driver or another C programmer to make the changes we need to get rotation working properly again.

In the mean time, if you need touchscreen rotation check out Sam Engstrom's perl script.  I posted a link to his web site in an earlier message (#21) in this thread.

---

### Post by CMEPTb on 2009-02-19
Hey everyone. Here is the update to the concertedrxn script so it would work in Intrepid:

```
#!/bin/bash

# Change to /tmp to avoid cluttering the current directory.
cd /tmp

# Install the packages we need for setting up the serial port and compiling the driver's source code.
sudo apt-get install -y setserial xserver-xorg-dev x11proto-core-dev x11proto-fonts-dev build-essential pkg-config libxrandr-dev

# Configure the serial port to which the touchscreen is attached.
sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfig

# Set it up so that the serial port will be properly configured at boot time.
echo -e '/dev/ttyS0 irq 4 port 0x220 autoconfig' | sudo tee /etc/serial.conf

# Download the driver's source code from the web site.
wget http://www.conan.de/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2

# Extract the source code from the file.
tar -jxf xf86-input-fujitouch-0.6.5.tar.bz2

# Change to the source code subdirectory.
cd xf86-input-fujitouch-0.6.5

# Back up the source code file that we need to edit.
cp fujitsu.c fujitsu.c.original

# Patch the source code to allow the driver to work in Intrepid.
sed -i '/xf86AlwaysCore/d' fujitsu.c
sed -i '/ansic/d' libtouch.c
sed -i 's/xf86memset/memset/' libtouch.c

# Compile the source code and install the driver. 
./configure --prefix=/usr && make && sudo make install

exit 0
```

Thanks to Syock from [http://ubuntuforums.org/showthread.php?t=944169](http://ubuntuforums.org/showthread.php?t=944169) and concertedrxn for the original

EDIT: My xorg.conf had the touchscreen sections commented out by update-manager, so don't forget to follow the original instructions by concertedrxn on the first page. I'm not sure if this script is even different from concertedrxn version, but that's what fixed my problem after Intrepid update.

Hope this helps someone.

---

### Post by Mocker on 2009-04-07
Does someone have a way of incorporating this into Intrepid, since it uses Hal rather than relying on xorg.conf to configure devices? I've looked at the Hal documentation and I can't figure out how to add support for a serial-based touchscreen.... none of the docs I read tells you how you actually select the device you're trying to create a configuration for (i.e. "I'm adding this mouse device, and its's located at /dev/ttyS0 and...").

As an alternative, can someone post a current, up-to-date xorg.conf file, if they still actually work with Intrepid?

---

### Post by Favux on 2009-04-07
Hi Mocker,

If you post your xorg.conf that you currently have in Intrepid I can give you and up-todate Intrepid xorg.conf with Wacom.  I can look at the ones in post #1 and #27.  Does your stylus have an eraser?  Does it have buttons.  If so how many?  From the xorg.conf I looked at you don't have touch, correct?

The 10-wacom.fdi file should give you stylus.  But it won't give you buttons, eraser or calibration with wacomcpl.

Which version of linuxwacom drivers do you have installed.  The default 0.8.1-4 version in Intrepid?  Have you installed wacom-tools?

---

### Post by aren55555 on 2009-04-28
I cannot get my touchscreen to work with the updated script provided. I am not sure where I am doing something wrong.

When I execute the command:
```
sh touchscreen.sh
```
I get this error in the console:
```
make  all-am
make[1]: Entering directory `/tmp/xf86-input-fujitouch-0.6.5'
if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -DXINPUT -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -g -O2 -MT fujitsu_drv_la-fujitsu.lo -MD -MP -MF ".deps/fujitsu_drv_la-fujitsu.Tpo" -c -o fujitsu_drv_la-fujitsu.lo `test -f 'fujitsu.c' || echo './'`fujitsu.c; \
	then mv -f ".deps/fujitsu_drv_la-fujitsu.Tpo" ".deps/fujitsu_drv_la-fujitsu.Plo"; else rm -f ".deps/fujitsu_drv_la-fujitsu.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I. -DXINPUT -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -g -O2 -MT fujitsu_drv_la-fujitsu.lo -MD -MP -MF .deps/fujitsu_drv_la-fujitsu.Tpo -c fujitsu.c  -fPIC -DPIC -o .libs/fujitsu_drv_la-fujitsu.o
fujitsu.c:32:25: error: xf86Version.h: No such file or directory
fujitsu.c:33:49: error: missing binary operator before token "("
fujitsu.c:71:25: error: xf86OSmouse.h: No such file or directory
fujitsu.c:125: warning: 'ModuleInfoRec' is deprecated
fujitsu.c:140: error: 'XF86_VERSION_CURRENT' undeclared here (not in a function)
fujitsu.c: In function 'Plug':
fujitsu.c:156: warning: 'xf86AddModuleInfo' is deprecated (declared at /usr/include/xorg/xf86.h:313)
fujitsu.c: In function 'DeviceInit':
fujitsu.c:334: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes integer from pointer without a cast
fujitsu.c:334: error: too many arguments to function 'InitValuatorClassDeviceStruct'
make[1]: *** [fujitsu_drv_la-fujitsu.lo] Error 1
make[1]: Leaving directory `/tmp/xf86-input-fujitouch-0.6.5'
make: *** [all] Error 2

```

Keep in mind that I am a fairly basic linux user running Ubuntu 9.04

Thanks for the help.

---

### Post by concertedrxn on 2009-04-29
I personally have stopped using the Fujitsu P-Series driver and am now using Sam Engstrom's Perl script, which you can find here: [http://samengstrom.com/nxl/3566/p1510_touchscreen_page.en.html](http://samengstrom.com/nxl/3566/p1510_touchscreen_page.en.html)

In order to use the script in Ubuntu, you will need to install several packages first, so open a terminal by going to "Applications-->Accessories-->Terminal" in the upper-left menu and enter or copy/paste the following:

```

sudo apt-get install setserial wacom-tools libxt-dev libxtst-dev

```

Then install the X11::GUITest module from CPAN in Perl:

```

sudo perl -MCPAN -e "install('X11::GUITest')"

```

Just accept the defaults when prompted by hitting "Enter".

You will need to set up the touchscreen serial device so the Perl driver can work with it.

```

sudo chmod a+rwx /dev/ttyS0
sudo setserial /dev/ttyS0 irq 4 port 0x220 autoconfig

```

And you will want to set it up so that the serial device will continue to work after a reboot:

```

echo -e '/dev/ttyS0 irq 4 port 0x220 autoconfig' | sudo tee -a /etc/serial.conf

```

Next, download [Sam Engstrom's Perl script]("http://samengstrom.com/nxl/7977/tablet6.en.pl") and save it somewhere in your executable path. I created a /home/$USER/bin directory and put it there, where "$USER" is your user login name.

Then try it out by pressing ALT-F2 and typing:

```
tablet6.en.pl
```

Wait for a few seconds for it to initialize and then touch the screen to see that it works.  If it does, you will want to go to "System-->Preferences-->Sessions" in Intrepid Ibex (8.10) or earlier or "System-->Preferences-->Startup Applications" in Jaunty Jackalope (9.04) to add an entry for it to start any time you log in.  In the program that opens just click "Add" and make a new entry with the command "tablet6.en.pl" (no quotes).

In Hardy, Sam Engstrom's driver wouldn't survive a suspend/resume cycle, but in Intrepid and Jaunty it does.

---

### Post by Mocker on 2009-05-12
concertedrxn,

Thanks! That worked for me undert Jaunty but I did run into a weird issue... after doing seterial once to set up the serial port, the perl script worked fine. However, from then on, it would die with a "no such device" error for /dev/ttyS0, even after fully shutting down and rebooting the machine. 

This seems like a device issue, since after issuing setserial, even doing a "cat < /dev/ttyS0" returned a device not available error. I took the setserial line out of /etc/serial.conf and rebooted, then ran the script... and it worked fine. Not sure if I messed something up somewhere, but if someone else is having the same issue, that's something to try.

But, I have the touchscreen working. Now on to rotation...

---

### Post by andrew frank on 2009-08-20
I have a Lifebook P1630 (similar to the P1620) and i tried the script from sam engstrom. it failed, because the P1630 (and the P1620) connect the touchscreen with usb, not serial. the error occurs when calling wacdum /dev/ttyS0 -- error wacomOpenTable - invalid argument.

i think it should be relatively easy to connect the usb touchscreen to an eventNN (NN = 1..9) and then use wacdump /dev/input/eventNN, but i am not certain exactly how. 

i got the p1630 working with another method (see my [blog]("http://andrewufrank.blogspot.com/2009/08/fujitsu-lifebook-p1630-touchscreen.html"))

---

### Post by Favux on 2009-08-20
Hi Andrew,

I'm not sure exactly what you're asking but Appendix 1 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  shows how we determine the usb by-path for usb Wacom tablet pc's.

---

### Post by jesusmolo on 2010-01-19
hi. I am new to linux. I have a Fujitsu P1510D and installed UBUNTU 9.1. This software is excellent but I'm a rookie. I could not install the tablet pc. I followed all the instructions in this forum and I do not work.  please help me.
**I write in terminal: **[COLOR=black]sh[/COLOR] [COLOR=black]touchscreen.sh[/COLOR]**get the message**: ERROR 2

sh: Can't open touchscreen.sh
root@dario-laptop:~# gedit touchscreen.sh
root@dario-laptop:~# sh touchscreen.sh
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
setserial ya está en su versión más reciente.
xserver-xorg-dev ya está en su versión más reciente.
x11proto-core-dev ya está en su versión más reciente.
x11proto-fonts-dev ya está en su versión más reciente.
build-essential ya está en su versión más reciente.
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  linux-headers-2.6.31-14 librsvg2-2.18-cil libgdata1.4-cil
  kdebase-workspace-libs4+5 erlang-esdl python-configobj libxosd2 python-bluez
  libsdl-ttf2.0-0 python-qt4-dbus libwnck2.20-cil libxnconfig9.0.3 xneur
  linux-headers-2.6.31-14-generic libnotify0.4-cil libgnomedesktop2.20-cil
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
-e /dev/ttyS0 irq 4 port 0x220 autoconfig
--2010-01-19 23:01:18--  [http://www.conan.de/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2](http://www.conan.de/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2)
Resolviendo [www.conan.de](www.conan.de)... 80.237.132.133
Conectando a [www.conan.de|80.237.132.133|:80](www.conan.de|80.237.132.133|:80)... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 216086 (211K) [application/x-tar]
Guardando: «xf86-input-fujitouch-0.6.5.tar.bz2»

100%[======================================>] 216.086     94,1K/s   en 2,2s    

2010-01-19 23:01:26 (94,1 KB/s) - `xf86-input-fujitouch-0.6.5.tar.bz2' guardado [216086/216086]

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for ANSI C header files... (cached) yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
make  all-am
make[1]: se ingresa al directorio `/tmp/xf86-input-fujitouch-0.6.5'
if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -DXINPUT -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -g -O2 -MT fujitsu_drv_la-fujitsu.lo -MD -MP -MF ".deps/fujitsu_drv_la-fujitsu.Tpo" -c -o fujitsu_drv_la-fujitsu.lo `test -f 'fujitsu.c' || echo './'`fujitsu.c; \
    then mv -f ".deps/fujitsu_drv_la-fujitsu.Tpo" ".deps/fujitsu_drv_la-fujitsu.Plo"; else rm -f ".deps/fujitsu_drv_la-fujitsu.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I. -DXINPUT -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -g -O2 -MT fujitsu_drv_la-fujitsu.lo -MD -MP -MF .deps/fujitsu_drv_la-fujitsu.Tpo -c fujitsu.c  -fPIC -DPIC -o .libs/fujitsu_drv_la-fujitsu.o
fujitsu.c:32:25: error: xf86Version.h: No such file or directory
fujitsu.c:33:49: error: missing binary operator before token "("
fujitsu.c:71:25: error: xf86OSmouse.h: No such file or directory
fujitsu.c:125: warning: 'ModuleInfoRec' is deprecated
fujitsu.c:140: error: 'XF86_VERSION_CURRENT' undeclared here (not in a function)
fujitsu.c: In function 'Plug':
fujitsu.c:156: warning: 'xf86AddModuleInfo' is deprecated (declared at /usr/include/xorg/xf86.h:313)
fujitsu.c: In function 'DeviceInit':
fujitsu.c:334: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected 'int' but argument is of type 'int (*)(struct _DeviceIntRec *, struct xTimecoord *, long unsigned int,  long unsigned int,  struct _Screen *, BOOL)'
fujitsu.c:334: error: too many arguments to function 'InitValuatorClassDeviceStruct'
make[1]: *** [fujitsu_drv_la-fujitsu.lo] Error 1
make[1]: se sale del directorio `/tmp/xf86-input-fujitouch-0.6.5'
make: *** [all] Error 2
/tmp


**Here is my xorg.conf:**

Section "Files"
EndSection

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "CoreKeyboard"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ImPS/2"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
# Uncomment to use MIddle Click + Mouse for scroll
# Option "EmulateWheel" "true"
# Option "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
    Identifier "Synaptics Touchpad"
    Driver "synaptics"
    Option "SendCoreEvents" "true"
    Option "Device" "/dev/psaux"
    Option "Protocol" "auto-dev"
    Option "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "stylus"
    Option "Device" "/dev/input/wacom"
    Option "Type" "stylus"
    Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "eraser"
    Option "Device" "/dev/input/wacom"
    Option "Type" "eraser"
    Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "cursor"
    Option "Device" "/dev/input/wacom"
    Option "Type" "cursor"
    Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
    Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Monitor "Generic Monitor"
Option "RandRRotation" "True"
DefaultDepth 24
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "touchscreen" "CorePointer"
InputDevice "dummy"
InputDevice "touchscreen"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
# InputDevice "Synaptics Touchpad"
EndSection

Section "InputDevice"
Identifier "dummy"
Driver "void"
Option "Device" "/dev/input/mice"
EndSection

Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "146"
    Option "MaxX" "4036"
    Option "MaxY" "3999"
    Option "SendCoreEvents" "On"
EndSection 


 please help me. and thanks for your attention

---

### Post by concertedrxn on 2010-02-25
For those using Jaunty or any later version of Ubuntu, please follow the instructions given in [message #37]("http://ubuntuforums.org/showpost.php?p=7180185&postcount=37") of this thread.  The old script given in message #4 will no longer work for the newer versions of Ubuntu.

---

### Post by Mocker on 2010-05-23
So, I installed Lucid netbook edition of my P1510D, and went to re-setup the touchscreen using Sam Engstrom's Perl script (see [post #37 in this thread]("http://ubuntuforums.org/showpost.php?p=7180185&postcount=37")), only to hit a snag: the wacom-tools package doesn't exist. I'm not sure why... there's a [Lucid launchpad page for the package]("https://launchpad.net/ubuntu/lucid/+package/wacom-tools"), but its status is "deleted." I've found some hard-to-follow bug threads that mention problems in Lucid with wacdump, so I wonder if the developers didn;t just punt and remove it rather than fixing it. There's a xserver-xorg-input-wacom package, which I installed, but it didn't have the wacdump utility that the Perl script uses to glue the tablet output into the X server (I've not dug into the script to figure out exactly how it works). 

Meanwhile, the fujitouch X driver [available from here]("http://www.conan.de/touchscreen/p-series.html") seems to be pretty much abandoned [according to this bug report]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/134401") (essentially, the Ubuntu developers are saying "gosh, somebody should do something... just not me.") 

So, I'm not sure which way to go. It would probably be easier to figure out where wacdump went to, or somehow replace its functionality rather than to try hacking a new version of the driver (or as the Ubuntu developers suggest, hack the driver code into one of the two existing touchpanel driver, neither of which really are appropriate since they aren't the same hardware-wise as the P1510D's hardware, as far as I can tell). It doesn't look like the functionality of the old fujitouch driver was incorporated anywhere else, so I doubt it's just a matter of tweaking settings for one of current drivers to work with the driver (the evtouch, for example, only works with USB deveices, where the P1510D's touchscreen is serial).

Any thoughts?

---

### Post by dwangoac on 2010-05-23
> **Mocker said:**
> ...only to hit a snag: the wacom-tools package doesn't exist. I'm not sure why... there's a [Lucid launchpad page for the package]("https://launchpad.net/ubuntu/lucid/+package/wacom-tools"), but its status is "deleted." 

I got it!  Mocker, thank you very much for posting the Launchpad link.  It turns out that there's a raw .deb file you can get there for the wacom-tools package.  Here's a direct link:

[http://launchpadlibrarian.net/33684766/wacom-tools_0.8.4.1-0ubuntu4_i386.deb](http://launchpadlibrarian.net/33684766/wacom-tools_0.8.4.1-0ubuntu4_i386.deb)

That package conflicts with the aforementioned xserver-xorg-input-wacom but performing an apt-get remove on that package allows wacom-tools to be installed.  From there the instructions from post #37 work correctly in Ubuntu 10.04 - I was able to get the tablet6.en.pl script to run and the touchscreen worked the same as it did in Ubuntu 9.10.

Anyone "backing in" to this thread will have a bit of a hard time following these instructions but hopefully this at least gets you going.  Good luck,

A.C.
******

---

### Post by concertedrxn on 2010-05-25
Instead of installing a package, I just went to the Linux Wacom project's web site and downloaded the latest tarball.  The tarball had precompiled binaries, so I just copied the precompiled wacdump to a directory on my path and made it executable.  I put it in $HOME/bin/, but you could copy it to /usr/bin if you want.  You'll find the Linux Wacom project's download page here: [http://linuxwacom.sourceforge.net/index.php/dl]("http://linuxwacom.sourceforge.net/index.php/dl").

---

### Post by kathleenhenri on 2010-06-26
I confess that I am an eager Linux devotee and am trying to install some form of ubuntu on every computer I can get my hands on - but am still learning and have been trying to follow post #37 but am stuck at this line:

[COLOR=Navy]"Next, download [Sam Engstrom's Perl script]("http://samengstrom.com/nxl/7977/tablet6.en.pl") and save it somewhere in your executable path. I created a /home/$USER/bin directory and put it there, where "$USER" is your user login name."[/COLOR]

Specifically, I am having trouble creating the directory to put the tablet6.en.pl into to make it executable.

Sorry for such a noob question, but would really appreciate some guidance.:confused: 
Many thanks.

---

### Post by kathleenhenri on 2010-07-06
> **kathleenhenri said:**
> I confess that I am an eager Linux devotee and am trying to install some form of ubuntu on every computer I can get my hands on - but am still learning and have been trying to follow post #37 but am stuck at this line:

[COLOR=Navy]"Next, download [Sam Engstrom's Perl script]("http://samengstrom.com/nxl/7977/tablet6.en.pl") and save it somewhere in your executable path. I created a /home/$USER/bin directory and put it there, where "$USER" is your user login name."[/COLOR]

Specifically, I am having trouble creating the directory to put the tablet6.en.pl into to make it executable.

Sorry for such a noob question, but would really appreciate some guidance.:confused: 
Many thanks.


After more searching I managed to figure out how to create an executable file. So for anyone out there running across this thread as I did, and perhaps with the same noob question, here is a solution.

Following the advice I found in this thread along with this link,
[http://doitfast4u.blogspot.com/2008/07/howto-get-touchscreen-working-on.html](http://doitfast4u.blogspot.com/2008/07/howto-get-touchscreen-working-on.html) I created the following in terminal:

```
sudo mkdir /opt/touchscreen
sudo chmod o+wx /opt/touchscreen
wget http://samengstrom.com/nxl/7977/tablet6.en.pl -P /opt/touchscreen/
```

This creates the /opt/touchscreen file, makes it executable and the third line downloads and executes the tablet6.en.pl file. 

Add the following "perl /opt/touchscreen/tablet6.en.pl" without quotes to  "System-->Preferences-->Startup Applications"

---

### Post by concertedrxn on 2010-07-10
Sorry for not replying sooner.  I just noticed your post.

I'm glad to see you found an answer, and it's great that you shared what you learned.  If you're interested in knowing what all the directories are for in a typical Linux filesystem hierarchy, you can learn more here: [Linux Filesystem Hierarchy]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/").  The directory "/opt/" is for software that's not part of the official distribution, so it's a good place for the touchscreen driver.

Regarding "/home/$USER/bin/", the "$USER" part is an environment variable holding your user name, so "/home/$USER/" is your home directory.  You could make a "bin/" directory in your home directory by opening a terminal and simply typing "mkdir bin".  Or, if you prefer to use the GUI, you could open your home directory by clicking the "Places" menu in the top GNOME panel and then clicking "Home Folder".  When Nautilus File Browser opens, you could then click on "File" and "Create New Folder" and name the new folder "bin".  (Notice how many more words were necessary to try to describe how to use the GUI to make a new directory! That's why you find most instructions in the forums make use of the command line terminal and text commands.)

---

### Post by kathleenhenri on 2010-08-18
> **concertedrxn said:**
> Sorry for not replying sooner.  I just noticed your post.

I'm glad to see you found an answer, and it's great that you shared what you learned.  If you're interested in knowing what all the directories are for in a typical Linux filesystem hierarchy, you can learn more here: [Linux Filesystem Hierarchy]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/").  The directory "/opt/" is for software that's not part of the official distribution, so it's a good place for the touchscreen driver.

Regarding "/home/$USER/bin/", the "$USER" part is an environment variable holding your user name, so "/home/$USER/" is your home directory.  You could make a "bin/" directory in your home directory by opening a terminal and simply typing "mkdir bin".  Or, if you prefer to use the GUI, you could open your home directory by clicking the "Places" menu in the top GNOME panel and then clicking "Home Folder".  When Nautilus File Browser opens, you could then click on "File" and "Create New Folder" and name the new folder "bin".  (Notice how many more words were necessary to try to describe how to use the GUI to make a new directory! That's why you find most instructions in the forums make use of the command line terminal and text commands.)

Thanks for the link. Most helpful. I'll probably be a noob for the rest of my life - but I have found that I learn this stuff best by finding an old (or new) computer and working through the challenges of getting everything to function in Linux.

Now back to the p1510d and figuring out how to get the stylus function to rotate with the screen. Most of my research settles on the idea of using a script that will stop the touchscreen and restart it again after it is rotated.

This guy seems to have had success with that.
[http://www.youtube.com/watch?v=say2u-yX1BM](http://www.youtube.com/watch?v=say2u-yX1BM)

His blog. Translated from Korean so it's a little hard to understand at times.
[http://translate.google.com/translate?hl=en&sl=ko&u=http://opensea.egloos.com/5101103&ei=o9FrTIHoLMaqlAfqvrxi&sa=X&oi=translate&ct=result&resnum=3&ved=0CBoQ7gEwAjgU&prev=/search%3Fq%3Dbugbear5%2Bp1510%26start%3D20%26hl%3Den%26sa%3DN%26prmd%3Dv](http://translate.google.com/translate?hl=en&sl=ko&u=http://opensea.egloos.com/5101103&ei=o9FrTIHoLMaqlAfqvrxi&sa=X&oi=translate&ct=result&resnum=3&ved=0CBoQ7gEwAjgU&prev=/search%3Fq%3Dbugbear5%2Bp1510%26start%3D20%26hl%3Den%26sa%3DN%26prmd%3Dv)

---

### Post by kathleenhenri on 2010-09-07
More solutions for rotating stylus along with screen rotation.

[http://ubuntuforums.org/showthread.php?t=1568147](http://ubuntuforums.org/showthread.php?t=1568147)

---

### Post by brianzinken on 2010-10-12
Hi, I am new to ubuntu and have been struggling with getting the touchscreen to work with the instructions listed on this thread.  I guess I will explain the steps I am doing, to see if someone can tell what I am doing wrong.
I start with a fresh install of ubuntu 10.04.
I install the package listed in comment 44.
I follow the instructions in comments in comment 37.
It seems like the X11::GUITest isn't installing correctly for me.  Perhaps I am missing a step that a more seasoned ubuntu user would catch.  
It is my understanding that I do not need the old driver, just sam engstrom's script.
Thanks,
Brian

---

### Post by neillmitchell on 2010-10-14
Okay, after reading many posts in various places, I got the touchscreen and screen swivel to work including touch re-calibrating on portrait/landscape screen switch.

Details in "Working on my P1510 under Maverick" post here:
[http://ubuntuforums.org/showthread.php?p=9971941#post9971941](http://ubuntuforums.org/showthread.php?p=9971941#post9971941)

Kudos to Albrechts for providing the patched debs.

Enjoy!

---

### Post by theSeinfeld on 2011-03-28
You can find the Conan packages build here:
[https://launchpad.net/~fujitouch/+archive/ppa/+packages](https://launchpad.net/~fujitouch/+archive/ppa/+packages)

They work fine for me (you still need to follow the instructions from Conan site here:
[http://www.conan.de/touchscreen/p-series.html](http://www.conan.de/touchscreen/p-series.html)

And make sure that your mouse is not the core pointer but instead the touch is...

Cheers,
Peter

---

### Post by Rootbrian on 2012-01-30
Sorry to bump this thread, but is there any way to get the touch screen working in ubuntu 11.10? I have the same fujitsu lifebook p1015d tablet and google doesn't have anything for it either. Since it uses gnome 3, there isn't an xorg.conf file anywhere. I could use some help, if there even is a way.

---

### Post by Rootbrian on 2012-01-30
I just don't want to use windows on this thing. I love the experience Linux offers.

---

### Post by danmiddle2 on 2012-01-31
I have long since got rid of mine... have you considered downgrading the version of Gnome?

---

### Post by Rootbrian on 2012-01-31
I would much prefer to stick to the latest. I don't want to use the 8.04 area of gnome on 11.10. I guess I'll stick to winXP on this tablet until a fix is made some day, or I acquire a newer one once the disk drive no longer works. Also have a question, would it work using a large compact flash card in place of the hard disk? Cause it would make for a shock-proof solution, but I don't know how long it would last in terms of write/erase cycles.

---

### Post by noor212 on 2012-05-31
Has any one had any luck getting the touchscreen to work on the new version (ubuntu 12)?

---

### Post by iCognac on 2012-07-08
noor212, i didn't get. I've tryed all the ways, but none of them earned. Sorry.
p1620 work out of the box.

---

### Post by Favux on 2012-07-08
Hi noor212 and iCognac,

If fujitouch has been deprecated have you tried placing the touchscreen on evdev and see if you can get it working on evdev?  Or was fujitouch a serial driver not a usb one?  I've forgotten.

---

