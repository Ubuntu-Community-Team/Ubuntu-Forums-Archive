---
title: "Touchpad won't work on my Acer"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by obi-nine on 2006-06-01
Hi folks,

I have an Acer 4652 LMi. About a month after I got it (and under Breezy) the touchpad went all erratic and then stopped working for about a week before mysteriously starting to work again.

About a month ago the same thing happened but this time it hasn't come back.

Today I finished upgrading to Dapper (YAY!) which has fixed my other main pain - refusing to come out of suspend properly, but my trackpad still doesn't work although it no longer seems to be giving the syslog error that it used to when I booted (something about "losing sync at byte 1").

I installed ksynaptics which gives me a control panel app to switch it on and off. When I toggle it gives me the following in my Xorg.log:

[I]Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found[/I]

But I'm still not getting any action from the pad itself.

Any ideas?

thanks,

obi-nine

---

### Post by ozorba on 2006-06-30
Have you tried Fn+F7?

---

### Post by evil_elman on 2006-06-30
I've got a very similar laptop with the following xorg (regarding input devices)

```

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "FastTaps" "1"
	Option	    "SHMConfig" "on"
EndSection

```

Instead of having problems with the touchpad itself I had problems with my external mouse not working on one of my three USB ports...

Also had problems before regarding the special touchpad features (scrolling, dragging windows on the touchpad and so on) which were all resolved by using the above configuration...

Especially important for me was 'SHMConfig' which I don't know what it does.
Also, using '/dev/input/mice' for both the external mouse and the touchpad wasn't a good idea, apparently...

And... Remember FN+F7 as mentioned above...

---

### Post by obi-nine on 2006-07-02
Yay... that FN+F7 did the trick!  Thanks so much.

obi9

---

