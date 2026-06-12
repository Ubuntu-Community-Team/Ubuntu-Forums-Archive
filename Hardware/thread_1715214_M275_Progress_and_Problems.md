---
title: "M275 Progress and Problems"
date: 2011-03-26
forum: Hardware
---

### Post by Fenderian_Mayhew on 2011-03-26
<<Post-Thought>>
With tablet PCs there are many wiring problems that may seem to be software related which are acutaly hardware related. after a few days of assistance from Favux I got out my screwdrivers and opened the PC up and without finding any fried chips pieced it back together having poked all screen > motherboard connectors and the tablet functionality came back. as for the 0hz problem [http://ubuntuforums.org/showthread.php?t=1594965](http://ubuntuforums.org/showthread.php?t=1594965).

so for anyone experencing m275 problems. after exausting all forms of software tests check your connectors.
<<end of line>>

this is the Gateway m275 P/N 3501738
Progress: with the initial install of 10.10 all was smothe.
[LIST]
[*]Display good
[*]Wacom good
[*]Network good
[*]Card reader good
[*]Optical drive good
[*]USB good
[/LIST]

Problems: after 4 months of perfect tablet operation I tryed to use a seccond monitor. The screen which had displayed as "Laptop" 1024X768 60HZ  under System>Prefrences>Monitors now displays as "Unknown" 1024X768 0HZ. Even after 3 re-installations, with a winXP install inbetween, the problem persisted. I than installed 9.04. it seemed to repair the problem. The "Laptop" 1024X768 60HZ came back, but no wacom support. however i knew that would happen. 9.04 required the user install wacom themselfs. I began the process of upgrades hoping to acheve 10.10 without errors. At 9.10 no problems, still no wacom. at 10.04.1 the system wouldn't even boot. the kernel that comes with 10.04.1 seems to give the m275 problems. so i booted with the 9.10 kernel and updated to 10.10. The 0hz problem came back. I cant explain why, but 10.10 and 10.04.1 have serious problems with the m275 hardware.

---

### Post by Favux on 2011-03-26
Hi Fenderian,

What release were you using where it worked 4 months without a problem?  You lost me.

I'd guess it is a problem with the video card/video driver.  You need to post what the chip set is and that will also give you something to google for a fix with.  Enter in a terminal:
```
lspci | grep VGA
```
I'm betting on an Intel GMA integrated motherboard video chipset that needs some xorg.conf configuration.

Karmic uses HAL/.fdi files for configuration.  Lucid and later uses xorg.conf.d/.conf files.  All use the xorg.conf.

---

### Post by Fenderian_Mayhew on 2011-03-26
Output-
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I was using the most up to date version of 10.10. As I said, It worked perfectly. from pen input to SD card reader.  I did every update without fail. and now the wacom driver wont activate. (the tablet function is serial based)

---

### Post by Favux on 2011-03-26
Just to be sure I follow you are you saying everything is OK on Maverick except the wacom part?

If so enter in a terminal:
```
xinput list
```
and
```
xsetwacom list
```
and post the outputs.

---

### Post by Fenderian_Mayhew on 2011-03-26
the problems are 

1: a display listed as unknown with 0hz refresh rate
2: no wacom detected.
[FONT=monospace]
[/FONT]xinput output
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
[FONT=monospace]
[/FONT]xsetwacom list output
Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet stylus STYLUS

---

### Post by Favux on 2011-03-26
The *xinput list* shows the digitizer:
```
&#9116; &#8627; Serial Wacom Tablet eraser id=11 [slave pointer (2)]
&#9116; &#8627; Serial Wacom Tablet stylus id=12 [slave pointer (2)]
```
More importantly the *xsetwacom list* shows the same input devices:
```
Serial Wacom Tablet eraser ERASER
Serial Wacom Tablet stylus STYLUS 
```
Which indicates it is on the Wacom X driver and should be working.  Did you configure the wacom digitizer somewhere like xorg.conf or with xsetwacom commands?

It's remotely possible your stylus is broken.  Did you recently drop it or step on it or something?  Do you have a spare?


You have an old Intel motherboard video chipset that has a rich history in linux:
> Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
aka the Intel 855GM.  There are several threads and Ubuntu wikis on how to deal with it.

I do have a couple of old xorg.conf's that might work.  Do you currently have an xorg.conf?  If so what's in it?  Do you know how to back it up and restore it from the command line if you break X messing with it?

---

### Post by Fenderian_Mayhew on 2011-03-26
> Did you configure the wacom digitizer somewhere like xorg.conf or with xsetwacom commands?

no configurations were needed in the first but i f you have a how to link for set wacom i will give it a try.

> It's remotely possible your stylus is broken.  Did you recently drop it or step on it or something?  Do you have a spare?


Only if both my spair and the one i use both got 86ED 

You have an old Intel motherboard video chipset that has a rich history in linux:

aka the Intel 855GM.  There are several threads and Ubuntu wikis on how to deal with it.

> I do have a couple of old xorg.conf's that might work.
Do you currently have an xorg.conf?

Not at the moment. but i can see i will need one

---

### Post by Favux on 2011-03-26
That's weird.  I don't understand why the stylus isn't responding.  You could try one of the serial tablet PC scripts in post # 2 of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562"), using just the stylus and eraser sections and your "device names".  See if that kick starts something.

Hopefully all you need is the Depth:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Subsection	"Display"
		Depth		24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen 0 "Screen0" 0 0
EndSection
```
or less likely:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"ForceEnablePipeA" "true"
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
```

---

### Post by Fenderian_Mayhew on 2011-03-27
I dont know what to do. 

The Graphics card recomendations worked well however, the Wacom still refuses to work. i decided to backgrade to ubuntu 8.04.4. the screen works no prob, however the wacom tablet screen is recongnised just not runing.
output for- xsetwacom list
Synaptics Touchpad pad       

output for- xsetwacom list
Synaptics Touchpad pad  

im going to try an arangement adjustment but i still am at a loss

---

### Post by Fenderian_Mayhew on 2011-03-27
xinput list
"Virtual core keyboard"    id=0    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Virtual core pointer"    id=1    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
"Generic Keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"<default pointer>"    id=3    [XExtensionPointer]
    Num_buttons is 9
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Synaptics Touchpad"    id=4    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is -1
        Resolution is 3
    Axis 1 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
"eraser"    id=5    [XExtensionPointer]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 28800
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 21760
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"stylus"    id=6    [XExtensionPointer]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 28800
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 21760
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1

---

### Post by Favux on 2011-03-27
Just to be sure, you installed Hardy (8.04.4)?

In that case you need to configure your Wacom digitizer through the xorg.conf.  Also the linuxwacom drivers at that point had just started supporting usb tablets and there were some bugs.  What version of linuxwacom (xserver-xorg-input-wacom & wacom-tools) does Synaptic Package Manager say you have?

Also post your current xorg.conf so we can add the wacom stuff to it.

---

### Post by Fenderian_Mayhew on 2011-03-27
> **Favux said:**
> Just to be sure, you installed Hardy (8.04.4)?

In that case you need to configure your Wacom digitizer through the xorg.conf.  Also the linuxwacom drivers at that point had just started supporting usb tablets and there were some bugs.  What version of linuxwacom (xserver-xorg-input-wacom & wacom-tools) does Synaptic Package Manager say you have?

1:0.7.9.8 on each


>  Also post your current xorg.conf so we can add the wacom stuff to it.

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
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
#    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
#    Option        "Device"        "/dev/input/wacom" # USB ONLY?
    Option        "Device"        "/dev/ttyS1"      # SERIAL ONLY
    Option "Mode" "Relative"
    Option        "Type"          "stylus"
    Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#    Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
#    Option        "Device"        "/dev/input/wacom" # USB ONLY?
    Option        "Device"        "/dev/ttyS1"      # SERIAL ONLY
    Option "Mode" "Relative"
    Option        "Type"          "eraser"
    Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#    Option        "USB"           "on"               # USB ONLY
EndSection


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice   "stylus"  "SendCoreEvents"
    InputDevice   "eraser"  "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

---

### Post by Fenderian_Mayhew on 2011-03-27
btw thanks for being so helpful

---

### Post by Favux on 2011-03-27
Alright assuming the wacom.rules in udev is there and includes your model for the symlinks all you need to do is reverse the comments for usb to serial in both the stylus and eraser section. So change:
```
# Option "Device" "/dev/input/wacom" # USB ONLY?
Option "Device" "/dev/ttyS1" # SERIAL ONLY
...
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
# Option "USB" "on" # USB ONLY
```
to
```
Option "Device" "/dev/input/wacom" # USB ONLY?
# Option "Device" "/dev/ttyS1" # SERIAL ONLY
...
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
Option "USB" "on" # USB ONLY
```
and reboot.  If needed we can install an updated linuxwacom and wacom.rules.

---

### Post by Fenderian_Mayhew on 2011-03-27
ok. done w/o success. 

how does one update the tools and rules

---

### Post by Favux on 2011-03-27
Let's try the simplest way and see if the Intrepid deb at the Wacom wiki will work in Hardy.  Just download it and double click on it.  If it doesn't work no harm done.  See:  [https://help.ubuntu.com/community/Wacom#Ubuntu%208.10%20%28Intrepid%20Ibex%29](https://help.ubuntu.com/community/Wacom#Ubuntu%208.10%20%28Intrepid%20Ibex%29)  Just use the deb for your install, 32-bit or 64-bit.

---

### Post by Fenderian_Mayhew on 2011-03-27
they both call for a dependency that is un-get able, however when i check synaptic they are already both installed

---

### Post by Fenderian_Mayhew on 2011-03-27
libix6 and xserver-xorg-core

---

### Post by Favux on 2011-03-27
OK, well it was a long shot.

Use the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") Section 1 to install the current linuxwacom which is 0.8.8-11.  That will include both Ubuntu packages.  Appendix 3 near the bottom tells you how to install the wacom.rules.  You'll need to check on the directory and number Hardy is using since I'm not in my Hardy install currently.  You can't use Ron's rules because they are for ATTRS and you need the SYSFS ones.  I just updated them:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Linuxwacom_HOWTO#60-wacom.rules_on_systems_using_SYSFS](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Linuxwacom_HOWTO#60-wacom.rules_on_systems_using_SYSFS)

---

### Post by Fenderian_Mayhew on 2011-03-27
part one granted me  a lsmod  with the below list on it.

wacom                  18048  0 
usbcore               146412  4 wacom,ehci_hcd,uhci_hcd

i will keep you updated on my progress

---

### Post by Fenderian_Mayhew on 2011-03-27
downloaded the wacom rules file but am un certan of what to do with it

---

### Post by Favux on 2011-03-27
I booted into Hardy to check.  Look in /etc/udev/rules.d for a 50-xserver-xorg-input-wacom.rules file.  If it's there make a back up.  Then edit or create it with:
```
gksudo gedit /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
```
and place the entire contents of the SYSFS wacom.rules you want into it.  Save and reboot.

---

### Post by Fenderian_Mayhew on 2011-03-27
overwrite or append?

---

### Post by Favux on 2011-03-27
Overwrite.  The newer one has a little script for touch devices in it.

---

### Post by Fenderian_Mayhew on 2011-03-27
i noticed that the focous was on usb based devices. i beleve mine is Serial. its a Tablet pc after all.

---

### Post by Favux on 2011-03-27
Sorry, right you are.  And I looked at the xorg.conf's yesterday didn't I, so no excuses.  Oops.  I guess I was thinking of the Gateway C-120, I think it was called which is usb.  There are usb tabletPCs too, I have one, the HP TX2000.

So reverse the serial to usb changes we made in the xorg.conf back to serial.  On the two sample M275 xorg.confs I have the serial port is not the standard ttyS0 it is ttyS1.  Hopefully that's all you need to change to get it working.  Nothing else we did should hurt anything.

---

### Post by Fenderian_Mayhew on 2011-03-27
i did the serial switch and wacdump'ed ttyS1 it came up as a tablet pc screen and everything but all my pens wont respond. i have 3. one nice one that has worked up to last monday (when i tryed to use a seccond screen) a battered one (worked same as the nice one), and a usb one (obviously hopeless but worth an attempt). im worried i fried the sensor.

---

### Post by Favux on 2011-03-27
Ouch!

I don't know if usb vs serial stylus makes a difference.  But you can break the electromagnetic coil in the stylus or a connection in it.  All 3 seems pretty unlikely though.

But unless you had an electrical surge your digitizer is probably OK.  More likely an internal connection from the digitizer to the motherboard is loose.  So my guess is it is an "easy" fix.  Although I suppose a capacitor or something could have blown.

If you had a Window install to check the hardware on that would help with the diagnostics.

---

### Post by Fenderian_Mayhew on 2011-03-27
problem is windows requires spicific drivers. and i dont have any of the discs
my next move will be surgery to see if something has gone loose. though i doubt that. the problem only started when i atached a seccond monitor. it was a "found" lcd. a good screen buti feel the problem was caused by that screen, i just cant figure why.

---

### Post by Fenderian_Mayhew on 2011-03-27
I dont know how but i opened up the laptop and after finding nothing it works

---

### Post by Favux on 2011-03-28
Outstanding!  You let the evil spirits out!  :)

---

