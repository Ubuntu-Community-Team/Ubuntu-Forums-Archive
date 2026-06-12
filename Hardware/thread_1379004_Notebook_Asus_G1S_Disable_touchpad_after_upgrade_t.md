---
title: "Notebook Asus G1S: Disable touchpad after upgrade to 9.10"
date: 2010-01-12
forum: Hardware
---

### Post by skaface on 2010-01-12
Hi there!

After the upgrade from 9.04 to 9.10 i can't disable the touchpad with the notebooks key anymore.

Till now this happened after every upgrade but was always solvable with the instructions on [this site]("http://asusg1s.wikidot.com/ubuntu-7-10#toc18").

I did the same thing after the upgrade to 9.10 but this time it's just not working.

In the xorg.conf i recognized that the following area was commented out (i just commented it in my self):
```
Section "InputDevice"
	Identifier    "Synaptics Touchpad"
	Driver        "synaptics"
	Option        "SendCoreEvents"    "true"
	Option        "Device"    "/dev/psaux"
	Option        "Protocol"    "auto-dev"
	Option        "HorizScrollDelta"    "0"
	Option         "SHMConfig" "true"
	Option         "CorePointer" "true"
EndSection
```

Above of this the following thing was mentioned:
> # commented out by update-manager, HAL is now used

Is there any other file which i have to edit now?

Thanks in advance,

mik

---

### Post by kerry_s on 2010-01-12
touchpad settings are under the mouse controls, you no longer have to touch xorg.conf at all.

---

### Post by skaface on 2010-01-12
Ok, there is a extra tab for the touchpad in this tool but i can't find a way to disable it at all.

I can "only" set the following:
- Disable touchpad while typing
- Enable mouse clicks with touchpad
- Some settings for the scrolling-mode

I also have the software-tool gsynaptics installed with which i can disable the touchpad. Unfortunately this setting isn't permanent, which means, that it turns itself automatically on again after some time after i've disabled it...

Usually i work with a mouse connected to the notebook so that i only need the touchpad really occasionally...

thks

---

### Post by kerry_s on 2010-01-13
read the gsynaptics man page, theres a command you add to startup that reloads the saved settings when you log in.

---

### Post by skaface on 2010-01-14
Thanks a lot for this tip!

At least now the touchpad is disabled by default after every restart and stays disabled till i enable it in the gsynaptics-software manually!

It may be not that important, but i'd still would like to know, how i could make the notebooks enable/disable touchpad-key work again!? If anybody has any idea, please let me know!

Thanks,

mik

---

### Post by asaturn on 2010-02-06
I have the same problem, but I don't think the above is an actual "solution" but more of a really bad work-around.

the real problem here is that the ASUS function keys are not recognized at all, and the touchpad has the wrong drivers loaded by default.

---

### Post by skaface on 2010-02-08
Hi!

In the meantime i just recognized, that the "solution" above doesn't even work either...

The touchpad is disabled after every restart, thats correct, but unfortunately it becomes enabled without any interaction from me after some "up-time" ;(

Please let me know if you find any real, helpful solution here!

Thanks!

---

