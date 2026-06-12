---
title: "Logitech MX620"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by Battie on 2007-09-03
Hello everyone.

I've been trying to get my Logitech MX620 to work properly.  I have seen many help pages for multi-button mice, but none for my specific mouse.  Trying to adapt the other pages for my mouse hasn't helped.

Actually, it should be pretty simple, because the only "special" thing I want to do is change the middle button from the scroll wheel click to the search button.  Unfortunately, xev doesn't report a button number for this button (and only this button).

I also tried using evdev following the mx1000 page, but I just got the XServer BSOD.

Anyone have any ideas for an unreported mouse button?  I can give you any other information you need.

Thanks!

---

### Post by raulih on 2007-11-17
Does anyone know how to get tilt working with MX620? I have set other buttons ok, but xev doesn't seem even to recognize tilting. Someone else has the same problem: [http://gentoo-wiki.com/Talk:HOWTO_Advanced_Mouse#Is_there_anyone_using_the_MX620.3F](http://gentoo-wiki.com/Talk:HOWTO_Advanced_Mouse#Is_there_anyone_using_the_MX620.3F)

---

### Post by _Stevie_ on 2008-01-19
yup it doesnt work as written in the gentoo wiki. 

1. install xte:   apt-get install xautomation
2. copy this content in ~/.xbindkeysrc

```
"/usr/bin/xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' &" # button 8, browser back (also works in nautilus)
m:0x0 + b:8

"/usr/bin/xte 'keydown Alt_L' 'key Right' 'keyup Alt_L' &" # button 9, browser forward (also works in nautilus)
m:0x0 + b:9

"/usr/bin/xte 'key Left'  &" # button 7, vertical scroll right
m:0x0 + b:7

"/usr/bin/xte 'key Right' &" # button 6, vertical scroll right
m:0x0 + b:6
```

3. execute xbindkeys automatically and put it in "sessions"
4. copy the following in your xorg.conf and comment out your old mouse settings or make a backup of your old xorg.conf:

```
Section "InputDevice"
	Identifier  "Logitech MX620"
   	Driver      "evdev"
   	Option      "Name" "Logitech USB Receiver"
	Option 	    "Resolution" "800"
   	Option      "CorePointer"
   	Option      "evBits" "+1-2"
   	Option      "keyBits" "~272-287"
   	Option      "relBits" "~0-2 ~6 ~8"
   	Option      "Buttons" "10"
   	Option      "WHEELRelativeAxisButtons" "4 5" # vertical wheel
   	Option      "ButtonMapping" "1 2 3 8 9 10"
EndSection

```

this makes work almost everything, only the search button doesnt :(
when using xev i get a keycode of 122. as it seams this doesnt send 
a button number. i already tried to assign a sh-script to this keycode but
it doesnt work.

any tips appreciated!

---

### Post by raulih on 2008-01-20
Thanks, have to try this some day, already forgot tilting.

I didn't need the search option... It's as easy to press ctrl+f cause you have to go to the keys anyway. I made the search button to open the home folder instead (System > Preferences > Keyboard shortcuts). =)

---

### Post by _Stevie_ on 2008-01-20
yeah the tilting works very good.
well i paid for 10 buttons, i wanted to use them all :D
for the search button... i found out how to make it work.
it didnt work by default, so i had to assign it with Xmodmap to "XF86Search".
finally i assigned a console-launch to the button, pretty useful :)

greets,

stevie

---

### Post by krojew on 2008-02-03
I have a problem. I commented out "Configured Mouse" section in xorg.conf and added "Logitech MX620". xserver seems to have a problem with it and starts in failsafe mode. I have no idea why. Can somebody help?

---

### Post by _Stevie_ on 2008-02-03
did you maybe forget to edit the last line?

 screen "Default Screen"
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	**Inputdevice	"Logitech MX620"	"CorePointer"**
	Inputdevice	"Synaptics Touchpad"

you have to edit this line as well.

---

### Post by krojew on 2008-02-03
Didn't help. X always starts in failsafe. My xorg.conf looks like this:

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
EndSection

# Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"true"
# EndSection

Section "InputDevice"
    Identifier  "Logitech MX620"
    Driver      "evdev"
    Option      "Name" "Logitech USB Receiver"
    Option 	    "Resolution" "800"
    Option      "CorePointer"
    Option      "evBits" "+1-2"
    Option      "keyBits" "~272-287"
    Option      "relBits" "~0-2 ~6 ~8"
    Option      "Buttons" "10"
    Option      "WHEELRelativeAxisButtons" "4 5" # vertical wheel
    Option      "ButtonMapping" "1 2 3 8 9 10"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	# Inputdevice	"Configured Mouse"
	Inputdevice "Logitech MX620" "CorePointer"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by _Stevie_ on 2008-02-03
phew, i actually cant find any problem in the xorg.conf.

but ill post mine, which is working 100 %.

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
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Logitech MX620"
	Driver		"evdev"
	Option		"Name"	"Logitech USB Receiver"
	Option		"Resolution"	"800"
	Option		"CorePointer"
	Option		"evBits"	"+1-2"
	Option		"keyBits"	"~272-287"
	Option		"relBits"	"~0-2 ~6 ~8"
	Option		"Buttons"	"10"
	Option		"WHEELRelativeAxisButtons"	"4 5"# vertical wheel
	Option		"ButtonMapping"	"1 2 3 8 9 10"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce Go 7600]"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce Go 7600]"
	Monitor		"Standardbildschirm"
	Defaultdepth	24
	Option		"Coolbits"	"1"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Logitech MX620"	"CorePointer"
	Inputdevice	"Synaptics Touchpad"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by krojew on 2008-02-03
I don't know what's wrong but it doesn't work for me :(

---

### Post by _Stevie_ on 2008-02-03
does the config work when you reactivate the old mouse settings?

---

### Post by krojew on 2008-02-03
yes

---

### Post by _Stevie_ on 2008-02-04
okay, at least the old config works.
but i really have no clue what it could be :(

maybe try to disable some entries of the config and
enable them step by step to find out what entry causes
the problem.

---

### Post by n_e_f on 2008-02-04
I had the same problem..
I tried again and again

I think what worked at the end was changing the Identifier to "Configured Mouse"
Make sure the "Identifier" section is as writen in:  Section "ServerLayout"


netanel

---

### Post by krojew on 2008-02-04
I've changed the identifier to "Configured Mouse" and no effect. xorg log says:

```
(II) evdev brain: Rescanning devices (1).
(EE) PreInit returned NULL for "ConfiguredMouse"
Atom 4, CARD32 4, unsigned long 8
```

---

### Post by samwisgg on 2008-02-19
Krojew,

you have to do add the following to the input section of the xorg.conf :

```
Section "InputDevice"
    Identifier  "Logitech MX620"
    Driver      "evdev"
    Option      "Name" "Logitech USB Receiver"
    Option       "Device" "/dev/input/event5"
    Option          "Resolution" "800"
    Option      "CorePointer"
    Option      "evBits" "+1-2"
    Option      "keyBits" "~272-287"
    Option      "relBits" "~0-2 ~6 ~8"
    Option      "Buttons" "10"
    Option      "WHEELRelativeAxisButtons" "4 5" # vertical wheel
    Option      "ButtonMapping" "1 2 3 8 9 10"
EndSection
```

The only line that I added with regard to your conf file is the one indicating the Device. It might be different for you regarding the event number to specify (event5 in my case) :

do a cat /proc/usb/input/devices and look for an entry that points to "Logitech USB receiver", mine gave the following :

```
I: Bus=0003 Vendor=046d Product=c521 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=mouse2 event5
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
```

The line for the Handlers indicates the event number, you'll have to use this number into you xorg.conf.
When I read this tread I applied the section as posted and had no reaction from my mx620 after. It reminded me of this 'device' thing from another thread and voilà everything worked !
Hope this is the same for you :)

Now I need to map my search button to the button 3 and I'm all set ...

---

### Post by krojew on 2008-02-19
Hmm... I don't have /proc/usb directory...

---

### Post by samwisgg on 2008-02-20
Krojew,

I made a typing mistake : you should look in /proc/bus/input. In there you will find the file 'devices'.

In the mean while, I restarted my PC and X server hung ! This can be corrected by using the "Dev Phys" in stead of "Device" option and provide the value "usb-0000:00:1d.1-2/input0" as is mentioned on the line "P:" of the /proc/bus/input/devices extract I mentioned in my previous post.

Hopefully a step closer to the solution.
PS. the above "Dev Phys" stuff I still have to try it out myself but it was what I found on [http://ubuntuforums.org/archive/index.php/t-181244.html]("http://ubuntuforums.org/archive/index.php/t-181244.html")

---

### Post by 65 mustang on 2008-04-01
None of the above worked for me only made X crash.  I think it was because it was using that other driver and not the "mouse" one.  I was able to get much better mouse control and the forward and back buttons working in firefox by using this mouse config.

```

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Resolution" "800"
    Option         "CorePointer"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

---

### Post by _Stevie_ on 2008-04-26
do the following:

```
find /dev/input/by-id/ -name "*event-mouse"
```

you will get something like this:

```
/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse
```

replace the following (the entry in my xorg.conf)

```
Option      "Name" "Logitech USB Receiver"
```

with the following entry:

```
Option      "Device" "/dev/input/by-id/your_finding_from_above"
```

do not delete your default mouse config:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver      	"mouse"
   	Option      	"CorePointer"
EndSection


```

instead add the other mouse entry as supplement.

also put this in "Server Layout":

```
Inputdevice	"Logitech MX620" "SendCoreEvents"
```




this should make it work!


good luck,

stevie

---

### Post by dimk1 on 2008-05-29
> **65 mustang said:**
> None of the above worked for me only made X crash.  I think it was because it was using that other driver and not the "mouse" one.  I was able to get much better mouse control and the forward and back buttons working in firefox by using this mouse config.

```

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Resolution" "800"
    Option         "CorePointer"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

That is true. This solution worked for me too in Firefox, but not in Dolphin. Any ideas?

---

### Post by xzero1 on 2008-07-12
Has anyone with an evdev setup been able to play nexuis?

---

