---
title: "Synaptics touchpad in Feisty"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by uyguy on 2007-04-21
Hi:

I have a problem with my touchpad.

I have a Toshiba Satellite A105-S4074 which has a synaptics touchpad. The touchpad is working, but only with essential features (no scrolling or tapping). I want to add scroll function to it.

I have read other posts where says to edit the Synaptic touchpad section in the xorg.conf file, but in my case there is no such section in the file.

Please help, i am a beginner so please try to explain in a step-by-step way.

Thanks.

---

### Post by hoopvillian on 2007-04-21
Same exact problem.  Same laptop.  Would appreciate help as well, please.  Tried installing and reinstalling the drivers and it still doesn't show up on the xorg file.

---

### Post by drmemory on 2007-04-25
I have essetially the same symptoms with the Synaptics touchpad in my Compaq 5307.

A similar problem, under WinXP on the same machine, was cured by downloading and
installing new irmware.  Perhaps there is a similar download somewhere for linux?

Curious that only Feisty needs it  The same touchpad worked fine with Dapper & Edgy.

Crossing my figers for somebody to come along who knows what to do.

---

### Post by uyguy on 2007-04-25
> Curious that only Feisty needs it The same touchpad worked fine with Dapper & Edgy.
I wasn't able to run my touchpad in edgy or dapper neither. Maybe it was only me :(

---

### Post by Sinkaiya on 2007-04-25
Hi guys. Why won't you add a touchpad section to your xorg.conf? Just do this:

1. sudo gedit /etc/X11/xorg.conf

2. Add this section below the keyboard or mouse one:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection

3. Add thisl line to the "ServerLayout" section (in my xorg.conf it is in the bottom of list):

InputDevice	"Synaptics Touchpad"

4. Save the file and reload. Hope it woll help.

Regards,

Sinkaiya

---

### Post by uyguy on 2007-04-25
Thanks Sinkaiya,

I just fixed my problem (reading other posts) :) 

I have to do exactly what you said.

Dont forget backup the xorg.conf file first, and make sure you have installed the synaptics driver (xserver-xorg-input-synaptics package).

Cheers :lolflag:

---

### Post by strabes on 2007-04-25
Here's a page listing all of the options on synaptics touchpads: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

---

### Post by Vabene on 2007-04-27
Sinkaiya you're great!!

---

### Post by ArKay on 2007-06-10
Excellent! Worked wonderfully. I can finally use my darned touchpad.  :)

Thanks a bunch.

Someday I gonna have to learn all the ins and outs of Linux s I can fix these things myself... I know enough from my days of Lynx and Pine to get along (barely) but configuration stuff is beyond me - for now.

---

