---
title: "disabling touchpad on ubuntu"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by scriv316 on 2007-04-17
Hey Everyone

I'm pretty new to ubuntu but im using 6.10 and I was wanting to disable the touchpad on ubuntu mainly due to the fact i barely brush the thumbpad with my thumb and it changes the position of the cursor, does anyone know how to accomplish this

Thanks ahead of time

---

### Post by Spartan.II.117 on 2007-04-17
have you checked the bios to see if there is an option there to disable it?

---

### Post by wuzzerd on 2007-04-17
You could install gsynaptics, for a gui tool or  tpconfig for a command line tool.

---

### Post by embrodak on 2007-04-17
Assuming you've already tried dooking around under System --> Preferences --> Mouse to adjust the sensitivity, first make sure you have the following in your /etc/X11/xorg.conf file:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

```

If so (particularly the SHMConfig cause that allows  you to mess with the settings without restarting X), the just run this command:

$synclient TouchpadOff=1

and to turn it back on, just run

$synclient TouchpadOff=0

---

### Post by jackmc on 2007-04-20
What can I do If I *dont *have that section in my xorg.conf?

My pad is working, but I have the ultrasensative issue :(

---

### Post by Chonnawonga on 2007-04-24
It's easy: just put it in there!

```
cd /etc/X11
sudo gedit xorg.conf
```

Make sure you create a backup first, and then add the above section with the other devices. You should be all ready to go.

Oh, and be careful: breaking your xorg.conf is bad.

Good luck!

---

### Post by jackmc on 2007-04-25
Thanks, I'm all sorted :)

The forums have saved me once again :)

---

### Post by ramjet_1953 on 2007-04-25
Before changing any config files, do you have any "hotkey" functions on your laptop for controlling things like, touchpad, volume, backlight intensity, external monitor, etc?

On my Acer 4101 I just use the lower, blue function+one of the upper funtion keys to do all of these things. This has worked for me since Dapper.

Regards,
Roger 8)

---

### Post by uterrorista on 2007-04-26
> **embrodak said:**
> Assuming you've already tried dooking around under System --> Preferences --> Mouse to adjust the sensitivity, first make sure you have the following in your /etc/X11/xorg.conf file:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

```

If so (particularly the SHMConfig cause that allows  you to mess with the settings without restarting X), the just run this command:

$synclient TouchpadOff=1

and to turn it back on, just run

$synclient TouchpadOff=0
this didn't work for me... why??

---

### Post by Chonnawonga on 2007-04-26
Ah, there is something missing from the above post:

You need to add
```
	InputDevice	"Synaptics Touchpad"
```
to the "ServerLayout" section near the bottom of your xorg.conf file.

For example, mine looks like this:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

Once you've made that change, restart. Does that help?

---

### Post by uterrorista on 2007-04-27
the problem was fixed by edit this

> 
        Option          "SHMConfig"             "on"
to 
>         Option          "SHMConfig"             "[COLOR="Red"]true[/COLOR]"

---

