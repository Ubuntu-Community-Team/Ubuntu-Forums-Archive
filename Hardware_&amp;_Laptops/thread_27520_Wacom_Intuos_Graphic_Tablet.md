---
title: "Wacom Intuos Graphic Tablet"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by Motomouse on 2005-04-16
Hi, is there anybody out there with an Intuos 3 Tablet working on hoary?

The Intuos 3 tablet is not working for me yet. I have identified /dev/input/event3 as the tablet (cat /dev/input/event3 produces output when i move the stylus or press the penbuttons). I changed xorg.conf accordingly and can activate the extended devices in gimp. But gimp is not responding to any tablet activity. Please add any information if you have an Intuos 3 working with hoary.

[http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue)

Thanks alot
Ralph

---

### Post by redrob on 2005-04-16
Ok, I may be able to help.
I'm assuming that you've got the wacom cursors working as a standard mouse in X windows...

What I had to do to get pressure in the Gimp was change some preferences:

In the window tiltled "The gimp" click on File->Preferences menu item.
The preferences window will appear.

In the Preferences window, Select the "Input devices" section.

Click on the "Configure extended input devices..." button.
The "Input" window will appear.

In the  "Input" window select the devices you want to use, and ensure their mode is
"Screen"

Press save, and you should be able to use your wacom devices.

Hope this solves your problem.

---

### Post by Motomouse on 2005-04-16
Thanks for your advice, but thats my problem: Everything is set up including the extended input devices in gimp, but gimp is not responding to the tablet. I think i have to build a custom kernel. I did this on gentoo already, but I would like to confirm that it is necessary for the intuos  3 on ubuntu hoary too. After that we can add the info to the wiki.

this is the wacdump output: 

MODEL=Wacom Intuos3 4x5                 ROM=1.0-2
CLS=USB  VNDR=Wacom  DEV=Intuos3  SUB=PTZ-430
BUTTON=+00000 (+00000 .. +00000)      RELWHEEL=+00000 (-00001 .. +00001)
    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=

only LEFT,MIDDLE and RIGHT get values from the tablet
but with xxd /dev/input/event3 i get reactions on the movement as well

Regards
Ralph

---

### Post by redrob on 2005-04-18
Sorry I couldn't help.
It certainly does look like you have serious problem with the kernel driver.
Maybe you should change the title of this thread (If you can ... dunno how this forum works) to reference Intuos 3 (I've got an Intuos 2), and somehow mention the kernel driver. You might be able to catch the eye of someone who can help you.

Also looks like a good time to file a bug report.

---

### Post by Motomouse on 2005-04-19
thanks for your help anyway  :)

---

### Post by graigsmith on 2005-04-27
have you added the device sections to the xorg.conf file?

if not see my post here about it here.
[http://ubuntuforums.org/showthread.php?t=24149](http://ubuntuforums.org/showthread.php?t=24149)

basically you need to add something similar to these, depending on What the devices label for your wacom is. and you need to change the mice device to mouse0 or whatever your mouse is on.  

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

#I also added these lines to the Section "ServerLayout".

InputDevice "cursor" "AlwaysCore"
InputDevice "stylus" "AlwaysCore"
InputDevice "eraser" "AlwaysCore"

---

### Post by graigsmith on 2005-04-27
oh yeah theres also one more device that you gotta add according to wacom linux project.
[http://linuxwacom.sourceforge.net/index.php/howto/x11](http://linuxwacom.sourceforge.net/index.php/howto/x11)

its for an intuos 3 tablet.

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"				
  Option        "Device"        "/dev/input/event0"
  Option        "Type"          "pad"
  Option        "USB"           "on"
EndSection

---

### Post by Motomouse on 2005-04-28
Hello, thanks for the response,

yes, the devices are set up in the xorg.conf and they show up in the gimp extended devices dialog. I think the problem is the mouse driver gets the control and not the wacom driver, like it is described in the mentioned howto and experienced by me already on my gentoo box. So you need probably a custom kernel for now. When I get time for testing i add my experiences.

Regards 
ralph

---

### Post by Motomouse on 2005-05-09
The Wacom Intuos 3 is working now on my Ubuntu 5.04.

I had to build a custom kernel.
I used the 2.6.10 Ubuntu kernel-sources and replaced 

evdev.c 
mousedev.c 
usbmouse.c 
hid-core.c 
wacom.c

with the according files from the linuxwacom project

[http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)

(When building a custom kernel, dont forget to create a new initrd.img if needed)

Have fun
Ralph

---

### Post by belfast-biker on 2005-05-09
[QUOTE=Motomouse]The Wacom Intuos 3 is working now on my Ubuntu 5.04.

I had to build a custom kernel.
I used the 2.6.10 Ubuntu kernel-sources and replaced 

evdev.c 
mousedev.c 
usbmouse.c 
hid-core.c 
wacom.c
[/QUOTE]



This is the sort of scary stuff that puts us Windows users off... ;)

Must get MP3's working next... was happy up until that that hurdle....

---

### Post by Motomouse on 2005-05-09
I changed my Desktop from Gentoo to Ubuntu because a lot of stuff works right out of the box for me. 

I changed it from Windows to GNU/Linux because it set me free.

Freedom can be scary :wink:

---

### Post by jonatin on 2005-07-25
[QUOTE=Motomouse]I changed my Desktop from Gentoo to Ubuntu because a lot of stuff works right out of the box for me. 

I changed it from Windows to GNU/Linux because it set me free.

Freedom can be scary :wink:[/QUOTE]

Yeah, I got tired of always seeming to need to emerge something just to get something else working.  Staring at the spew from a compiler isn't how I felt like spending my weekends.  I'll take being behind the 'bleeding edge' power curve for that "it just works" feeling.

<ahem> Now if only wacom would "just work."

I had all of these wacom problems on my iBook and my old x86 machine... and I never had to mess with the kernel though.  I had to carefully set my xorg.conf.  IIRC, setting "CorePointer" on /dev/input/mice was stealing the wacom events from the tablet and squashing them, rather than passing them to the GIMP.

---

### Post by Motomouse on 2005-07-25
I think it depends on the wacom tablet you try to connect. If it is not a new one, it should be detected by the standard kernel. 

regards 
ralph

---

### Post by kxs on 2005-10-21
My Intuos.3 tablet works under Breezy, but express keys don`t. I`ve built and installed esxpresskeys package-0.2.4 from this site:
[http://web.telia.com/~u46133770/wacom/index.html]("http://web.telia.com/~u46133770/wacom/index.html")
After "expresskeys pad" I get "expresskeys ERROR: Can not find pad device: pad". Also, there`s no "pad device" in GIMP, only eraser, stylus and cursor. What to do? :confused:

---

