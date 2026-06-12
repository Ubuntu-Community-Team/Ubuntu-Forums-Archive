---
title: "Logitech MX1000 Mouse and Logitech MX5000 Keyboard button Gutsy.  I've tried others"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by Mysticle31 on 2007-12-03
I would really like to have my MX5000 keyboard and MX1000 mouse work in Gutsy. 

I have tried MANY howtos that either do nothing or cause X not to start.  

The Mouse
I would like as many buttons to work as possible.  However back and forward are required.  It would be nice if the task switcher button would work.

My keyboard
Already works.  The only thing I would like is the media button to launch Amarok or whataver I make my media player.  I would also like the zoom button to work.  Perhaps enable the zoom program?

Volume sliders, play, pause..etc already work by default.

Also, sometimes the mouse and keyboard "forget" to connect.

Any ideas?

---

### Post by doug1212 on 2007-12-08
Just to add to the mountain of words about the mx1000, here is my mouse config.
I have not (yet) needed to resort to playing with udev rules it seems to be holding after reboots.

As per previous guides:

"sudo apt-get install xbindkeys xmacro xvkbd"

Back up /etc/X11/xorg.conf.

"sudo nano /etc/X11/xorg.conf"

I took the options from the example in man evdev.

```
Section "InputDevice"
        Identifier      "Configured Mouse" #MX1000
        Driver          "evdev"
	Option "Phys" "usb-0000:00:02.0-6/input0" #from cat /proc/bus/input/devices
	Option "Name" "Logitech USB RECEIVER" #from cat /proc/bus/input/devices
        Option "evBits" "+1-2" #from man evdev page example
        Option "keyBits" "~272-287"
        Option "relBits" "~0-2 ~6 ~8"
        Option "Pass" "3"
EndSection
```

```
Inputdevice     "Configured Mouse" "SendCoreEvents"
```


Edit: ~.xbindkeys

```
# Backward and Forward buttons
"xvkbd -text "\[Alt_L]\[Left]""
  m:0x10 + b:8
"xvkbd -text "\[Alt_L]\[Right]""
  m:0x10 + b:9
"echo ButtonRelease 10 ButtonPress 3 ButtonRelease 3 | xmacroplay -d 0 :0.0"
  b:10
"echo ButtonRelease 11 ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonRelease 12 ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonRelease 13 ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonRelease 14 ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```


Add xbindkeys to starup menu in sessions.

Set the options in firefox' about:config.

mousewheel.horizscroll.withnokey.action to "0"
mousewheel.withcontrolkey.sysnumlines to "true"

Doug.

---

### Post by daou on 2007-12-09
You may want to have a look at btnx for the mouse: [btnx thread]("http://ubuntuforums.org/showthread.php?t=455656")
[btnx home]("http://www.ollisalonen.com/btnx")
If you do try it, make sure to have a look at the manual's troubleshooting section for good xorg.conf values, especially if you have tried other howto's.

---

### Post by Mysticle31 on 2007-12-15
Thanks for the tips.  I have thought of installing festy for the better mouse support :P

My mouse and keyboard are bluetooth.  That makes getting my addresses are different right?


I: Bus=0005 Vendor=046d Product=b003 Version=4310
N: Name="Logitech MX1000 mouse"
P: Phys=00:07:61:47:28:3D
S: Sysfs=/class/input/input8
U: Uniq=00:07:61:4D:02:83
H: Handlers=mouse3 event8 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143


Xorg need decimal?

I have discovered that gutsy does support 7 mouse buttons.  The only thing I lose is auto-scroll, left and right scroll, and the "task switch" button.

---

### Post by Redmumba on 2007-12-17
This was KILLING me, I tried several methods both on here, on the Ubuntu wiki, and elsewhere, but this is the only one that worked.

[http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Logitech_MX1000](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Logitech_MX1000)

Literally required nothing more.  No additional modifications except the xorg.conf and the xmodmap lines.

---

### Post by p-stone on 2008-01-27
I have this mouse and keyboard combo. It works well enough except whenever I reboot I need to unplug the usb dongle and plug it back in to set them to usb emulation mode, rather than bluetooth (or so I understand) anyway, I'm wondering if there's a way I could make some sort of startup script that would automatically do this for me at boot. Does anyone know how to do something of this nature?
Thanks in advance

---

