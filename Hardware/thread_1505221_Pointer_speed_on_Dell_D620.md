---
title: "Pointer speed on Dell D620"
date: 2010-06-08
forum: Hardware
---

### Post by Astro96 on 2010-06-08
I recently upgraded to 10.04 and am having some trouble with my mouse pointer speed.  I was able to use my old xorg.conf to set all of my touchpad settings, but can't seem to get the "pointing stick" mouse to go fast enough.  So far I've tried changing the settings in System > Preferences > Mouse, using xinput set-prop, and using xset m, all with little success.

I saw some people were able to use HAL settings -- can anyone point me to a good resource for how to set that up, or will it only work for changing DPI settings? (DPI is not relevant for me because I'm trying to fix the pointing stick speed, not a USB mouse.)


Thanks!


Andy

---

### Post by Astro96 on 2010-06-09
After a few more hours of experimentation, I managed to get something decent.  I created a file that is run on gnome login that does the following:

```

xinput set-prop "DualPoint Stick" "Device Accel Profile" 6
xinput set-prop "DualPoint Stick" "Device Accel Velocity Scaling" 10

```

The key was to use Accel Profile 6 which feels much more correct for me.  If you are having a similar problem, to try to experiment run

```

xinput list

```

to see what your input devices are and then use

```

xinput list-props "<device name>"

```

to see what options you can change.  Finally, use

```

xinput set-prop "<device name>" "<property name>" <value>

```

to set the property.

Andy

---

### Post by Astro96 on 2010-06-09
Sadly, that doesn't work through a suspend/resume cycle.  Gah.

Turns out a better way is to put the parameters in your xorg.conf:

```

Section "InputDevice"
        Identifier      "Mouse1"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mouse1"
        Option          "Protocol"              "auto"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
	Option		"AccelerationProfile"	"6"
	Option		"VelocityScaling"	"10"
EndSection

```

I've attached my full xorg.conf that includes touchpad configuration as well for the Dell D620.  Hopefully it will be useful to someone.



Andy

---

