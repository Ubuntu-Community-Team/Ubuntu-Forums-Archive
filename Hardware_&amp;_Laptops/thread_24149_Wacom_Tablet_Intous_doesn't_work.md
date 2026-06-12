---
title: "Wacom Tablet Intous doesn't work?"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by kfc on 2005-04-05
Hi guys,
I've a problem with setting up my Wacom Tablet Intous. I've tried to follow [http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue) as close as possible. 

First I did the blacklist adding the evdev line. restart, wacom still the same, i can sketch with it but no pressure sensitivity.

Things getting a little messy when I come to to 4th part where "Go to /sys/bus/usb grep for WACOM..."

result that i've got is "
grep: warning: devices/usb3/driver/usb1/1-0:1.0/driver/3-0:1.0/driver: recursive directory loop

grep: warning: devices/usb3/driver/usb1/1-0:1.0/driver/2-0:1.0/driver: recursive directory loop

grep: warning: devices/usb3/driver/usb1/1-0:1.0/driver/1-0:1.0: recursive directory loop

grep: warning: devices/usb3/driver/usb1/driver: recursive directory loop

grep: warning: devices/2-0:1.0/driver/5-0:1.0/driver: recursive directory loop

grep: warning: devices/2-0:1.0/driver/4-0:1.0/driver: recursive directory loop

grep: warning: devices/2-0:1.0/driver/3-0:1.0/driver: recursive directory loop

grep: warning: devices/2-0:1.0/driver/2-0:1.0: recursive directory loop

grep: warning: devices/2-0:1.0/driver/1-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/5-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/4-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/3-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/2-0:1.0: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/1-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/driver/1-2/1-2:1.0/driver/1-2:1.0: recursive directory loop

grep: warning: devices/usb2/driver/1-2/driver: recursive directory loop

grep: warning: devices/usb2/driver/1-1/1-1:1.0/driver/1-1:1.0: recursive directory loop

grep: warning: devices/usb2/driver/1-1/driver: recursive directory loop

grep: warning: devices/usb2/driver/usb5/5-0:1.0/driver/5-0:1.0: recursive directory loop

grep: warning: devices/usb2/driver/usb5/5-0:1.0/driver/4-0:1.0/driver: recursive directory loop......"

Which is totally different from what I saw from Wiki.
So i took a guess by testing the devices one by one and indentified that 1-1 is my intous device (by using cat devices/1-1) 
I've followed the udev.rules edit and replace product with the name returned from "cat devices/1-1". I've also configured xorg.conf for the required settings. 

But after the restart, my wacom still react the same. no pressure sensitivity and still the size mapping isn't fully maximized to the screen. 
I've checked /dev/ and "wacom0" isn't in this directory at all. I've heard someone mentioned something about checking whether wacom0 is exisit in the /dev/. I hope someone can give me an answer because i don wanna switch to another distro just to make the wacom work.
sigh....


KFC

---

### Post by kfc on 2005-04-06
[QUOTE=kfc]Hi guys,
I've a problem with setting up my Wacom Tablet Intous. I've tried to follow [http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue) as close as possible. 

First I did the blacklist adding the evdev line. restart, wacom still the same, i can sketch with it but no pressure sensitivity.

Things getting a little messy when I come to to 4th part where "Go to /sys/bus/usb grep for WACOM..."

result that i've got is "
grep: warning: devices/usb3/driver/usb1/1-0:1.0/driver/3-0:1.0/driver: recursive directory loop

grep: warning: devices/usb3/driver/usb1/1-0:1.0/driver/2-0:1.0/driver: recursive directory loop

grep: warning: devices/usb3/driver/usb1/1-0:1.0/driver/1-0:1.0: recursive directory loop

grep: warning: devices/usb3/driver/usb1/driver: recursive directory loop

grep: warning: devices/2-0:1.0/driver/5-0:1.0/driver: recursive directory loop

grep: warning: devices/2-0:1.0/driver/4-0:1.0/driver: recursive directory loop

grep: warning: devices/2-0:1.0/driver/3-0:1.0/driver: recursive directory loop

grep: warning: devices/2-0:1.0/driver/2-0:1.0: recursive directory loop

grep: warning: devices/2-0:1.0/driver/1-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/5-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/4-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/3-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/2-0:1.0: recursive directory loop

grep: warning: devices/usb2/2-0:1.0/driver/1-0:1.0/driver: recursive directory loop

grep: warning: devices/usb2/driver/1-2/1-2:1.0/driver/1-2:1.0: recursive directory loop

grep: warning: devices/usb2/driver/1-2/driver: recursive directory loop

grep: warning: devices/usb2/driver/1-1/1-1:1.0/driver/1-1:1.0: recursive directory loop

grep: warning: devices/usb2/driver/1-1/driver: recursive directory loop

grep: warning: devices/usb2/driver/usb5/5-0:1.0/driver/5-0:1.0: recursive directory loop

grep: warning: devices/usb2/driver/usb5/5-0:1.0/driver/4-0:1.0/driver: recursive directory loop......"

Which is totally different from what I saw from Wiki.
So i took a guess by testing the devices one by one and indentified that 1-1 is my intous device (by using cat devices/1-1) 
I've followed the udev.rules edit and replace product with the name returned from "cat devices/1-1". I've also configured xorg.conf for the required settings. 

But after the restart, my wacom still react the same. no pressure sensitivity and still the size mapping isn't fully maximized to the screen. 
I've checked /dev/ and "wacom0" isn't in this directory at all. I've heard someone mentioned something about checking whether wacom0 is exisit in the /dev/. I hope someone can give me an answer because i don wanna switch to another distro just to make the wacom work.
sigh....


KFC[/QUOTE]
 ah... i've got it fixxed.
seems like in hoary, i don even have to worry about blacklist and evdev.
just add the correct settings in /etc/X11/xorg.conf
everything is solved.
as for the device setting. all i have to do is 
 $ sudo cat /dev/inpunt/event(num) 
and doodling on the tablet. If you get screenfull's of garbage it is your tablet (remember the (num) you used.

For now however, add the InputDevice sections to your XF86Config file. This assumes you are running XFree86 4.x. On some distributions, this file is called XF86Config-4. Notice that the serial and USB configurations are different, so only include the appropriate lines. For Tablet PCs, options "Device" and "ForceDevice" should be included. You should also change the device (e.g. ttyS0) to the correct one for your tablet; the default serial and USB devices are given. All the new driver options are listed in the manual page below.

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"				 # Intuos3 or Cintiq 21UX
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Seems like there's no need to install any wacom driver in default. and there's no need to compile the kernal at all.

way to go Ubuntu!!

---

### Post by graigsmith on 2005-04-07
[QUOTE=kfc]ah... i've got it fixxed.
seems like in hoary, i don even have to worry about blacklist and evdev.
just add the correct settings in /etc/X11/xorg.conf
everything is solved.
as for the device setting. all i have to do is 
 $ sudo cat /dev/inpunt/event(num) 
and doodling on the tablet. If you get screenfull's of garbage it is your tablet (remember the (num) you used.

For now however, add the InputDevice sections to your XF86Config file. This assumes you are running XFree86 4.x. On some distributions, this file is called XF86Config-4. Notice that the serial and USB configurations are different, so only include the appropriate lines. For Tablet PCs, options "Device" and "ForceDevice" should be included. You should also change the device (e.g. ttyS0) to the correct one for your tablet; the default serial and USB devices are given. All the new driver options are listed in the manual page below.

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"				 # Intuos3 or Cintiq 21UX
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Seems like there's no need to install any wacom driver in default. and there's no need to compile the kernal at all.

way to go Ubuntu!![/QUOTE]
 COOL i will have to try that out.

what would i enter for my tablet?  i have an intuos 2 tablet thats 6x8.

---

### Post by zeus on 2005-04-07
[QUOTE=graigsmith]COOL i will have to try that out.

what would i enter for my tablet?  i have an intuos 2 tablet thats 6x8.[/QUOTE]
 I have wacom graphire 2 and 3. I add the xorg.conf ass you suggested, no luck. And than i read the ubuntu wacon wiki page, and it said to add this line:

#Wacom Tablet
 BUS="usb" , SYSFS{manufacturer}="WACOM",SYSFS{product}="FT-0405-UV1.4-1", NAME="wacom0"

I'd replaced the product ID to graphire.

So far my wacom pressure still doesn't work. 

Here's my xorg config.
# Wacom

Section "InputDevice"
	Identifier 	"cursor"
	Driver		"Wacom"
	Option		"Device" "dev/input/event0"
	Option 		"Type" "cursor"
	Option		"USB" "on"
EndSection

Section "InputDevice"
	Identifier 	"stylus"
	Driver		"Wacom"
	Option		"Device" "dev/input/event0"
	Option 		"Type" "stylus"
	Option		"USB" "on"
EndSection

Section "InputDevice"
	Identifier 	"eraser"
	Driver		"Wacom"
	Option		"Device" "dev/input/event0"
	Option 		"Type" "eraser"
	Option		"USB" "on"
EndSection
# Wacom End

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
#wacom events
	InputDevice	"cursor" "SendCoreEvents"
	InputDevice	"stylus" "SendCoreEvents"
	InputDevice	"eraser" "SendCoreEvents"
EndSection

---

### Post by graigsmith on 2005-04-08
OMFG i got it working with pressure sensitivity!
in addition to adding what you wrote at the top.
the wacom page suggested adding some different things
[http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)

check out that and look at chapters 5.  they really explain how to get this working.  Seems that ubuntu comes with the driver for wacom, its just you gotta configure it.

heres what i added to my xorg.conf file

i added this below the mouse device.

Section "InputDevice"
  Identifier    "cursor"
  Driver 	"wacom"
  Option        "Device"        "/dev/input/event4"
  Option        "Type"          "cursor"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Identifier    "stylus"
  Driver	"wacom"
  Option        "Device"        "/dev/input/event4"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Identifier    "eraser"
  Driver   	"wacom"
  Option        "Device"        "/dev/input/event4"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
EndSection


I also added these lines to the server layout section

        InputDevice   	"cursor"
        InputDevice    	"stylus"
        InputDevice    	"eraser"


THEN reboot X with ctrl-alt-backspace, and go into gimp. then to enable the tablet you have to do this.

file, preferences, input devices, configure extended input devices

then under devices you will have 3 settings cursor erasor and stylus.  set them from disabled to screen.

now i get pressure sensitivity in gimp

---

### Post by graigsmith on 2005-04-08
now i am only having ONE problem,  the tablet mouse cursor is being ACCELERATED by the mouse software :(  

how do i fix this?

---

### Post by graigsmith on 2005-04-09
OK i fixed it, its working PERFECTLY now :)

heres what i did.

i changed the mouse section device from mice to mouse0, you have to test your devices and my mouse is on mouse0, so thats what i changed the device to.
after i did this i restarted x, and my tablet was no longer working.  i then changed these lines that i added earlier to

        InputDevice   	"cursor"	"AlwaysCore"
        InputDevice    	"stylus"	"AlwaysCore"
        InputDevice    	"eraser"	"AlwaysCore"

and once i added always core on the end, and restarted X, the wacom tablet started working flawlessly.  :)

---

### Post by MetalMusicAddict on 2005-04-09
Thank you guys SO much. I have a Graphire 2 and this worked PERFECTLY! ;)

> Heres what i added to my xorg.conf file. (also workes for XF86)

I added this below Section "InputDevice" under the "Configured Mouse".

----------------------------------------------------------------------------------------------
Section "InputDevice"
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/event4"
        Option "Type" "cursor"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/event4"
        Option "Type" "stylus"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/event4"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection
----------------------------------------------------------------------------------------------

I also added these lines to the Section "ServerLayout".

----------------------------------------------------------------------------------------------
         InputDevice "cursor" "AlwaysCore"
         InputDevice "stylus" "AlwaysCore"
         InputDevice "eraser" "AlwaysCore"
----------------------------------------------------------------------------------------------

Then Reboot or restart X with ctrl-alt-backspace and launch The GIMP. 

_Then to enable the tablet you have to do this:_

File> Preferences> Input Devices> "Configure Extended Input Devices".

Then under "Device" you will have 3 settings: cursor, eraser and stylus. Set them from "Disabled" to "Screen".

Now i get pressure sensitivity in The GIMP.
*Posts combined and edited to show what I used.

---

### Post by graigsmith on 2005-04-09
Also don't forget to change the mice device to mouse0 or mouse1,  the wacom site says that all pointer devices go thru mice, and if you have your main pointer set to mice, instead of mouse0 for your mouse it will cause problems like not being able to click with your mouse or your tablet.  Apparently this is an extra step you gotta do if your mouse is usb, and your tablet is usb.

---

### Post by kxs on 2005-10-21
[QUOTE=kfc]ah... i've got it fixxed.
seems like in hoary, i don even have to worry about blacklist and evdev.
just add the correct settings in /etc/X11/xorg.conf
everything is solved.
[/QUOTE]

does your intuos` express keys work? if so, how did you get it work?

---

