---
title: "How do I deactivate touchpad?"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by graabein on 2006-02-18
Hullo,

I have installed breezy on an old laptop and that's sweet but my ps2 mouse runs amock every now and then when it gets intensive (usual) mouse movements or when I haven't touched it for a while. I spoke with some friends and they suggested deactivating the touchpad... so, how do I do that?

Thanks!

---

### Post by moephan on 2006-02-18
I'm far from an expert here, but I think the general approach is to edit /etc/X11/xorg.conf. For example, I have a touchpad that I always seemd to be tapping while I was typing, so I edit xorg.config to turn of the tapping function:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"	
	Option		"MaxTapTime"		"0"
EndSection

```

If I remember correctly, it was setting MaxTapTime to 0 that did the trick. Of course, you are running different hardware, so the etries will be different, but I think the general approach is still the same.

If you do decide to edit xorg.config, as always, make sure you create a BACKUP first.

HTH.

Cheers, Rick

---

### Post by SolPhoenix on 2006-02-18
Cool!  Thanks to graabein for asking this question and to moephan for answering!
I've always wondered how to turn of tap-to-click.  If I even had my hands anywhere near the touchpad (not even on it), it seemed that it'd click and mess up whatever I was doing.

---

### Post by graabein on 2006-02-22
Thanks for the help but I just discovered that I'm actually quite comfortable with using the touchpad and not hooking up the ps/2 mouse at all! I copied the xorg.conf changes in case I want to go back.

---

### Post by surfgeek on 2006-04-13
[QUOTE=moephan]I'm far from an expert here, but I think the general approach is to edit /etc/X11/xorg.conf. For example, I have a touchpad that I always seemd to be tapping while I was typing, so I edit xorg.config to turn of the tapping function:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"	
	Option		"MaxTapTime"		"0"
EndSection

```

If I remember correctly, it was setting MaxTapTime to 0 that did the trick. Of course, you are running different hardware, so the etries will be different, but I think the general approach is still the same.

If you do decide to edit xorg.config, as always, make sure you create a BACKUP first.

HTH.

Cheers, Rick[/QUOTE]


Thank you,  Now I love my linux machine.

I was going mad with the touchpad...

:p :p :p :p

---

