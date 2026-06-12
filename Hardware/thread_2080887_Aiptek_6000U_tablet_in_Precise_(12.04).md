---
title: "Aiptek 6000U tablet in Precise (12.04)"
date: 2012-11-05
forum: Hardware
---

### Post by DrPotoroo on 2012-11-05
I've been able to follow instructions in these threads and on the Ubuntu community help wiki Aiptek page to get my old Aiptek tablet working in 12.04 - partially. However, I have the often mentioned problem that once I press on the stylus it doesn't register the pen being lifted. In gimp I can see the pressure sensitivity is working, but once I'm drawing I can't stop. It also messes with the buttons of my other pointers, so they don't register any clicks.

I have a feeling the problem could be the tablet simultaneously sending events as a tablet via /dev/input/eventX and as a mouse through the aggregate device /dev/input/mice. I have this feeling because years ago when I had this tablet working in linux changing my mouse device in X to something like /dev/input/mouse0 fixed the problem.

The difficulty I have in testing this theory is that I can't work out how to do this with the new way Xorg configurations work. Can anyone tell me how to force Xorg to NOT use /dev/input/mice?

---

### Post by Favux on 2012-11-05
Hi DrPotoroo,

Since these tablets are often rebranded let's find out who makes it and what model it is.  In a terminal run:
```
lsusb
```
and please post the output.  Or at least the tablet line output.

---

### Post by DrPotoroo on 2012-11-05
lsusb gives me the following line for the tablet: 
> Bus 002 Device 003: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet

Also, I did:
```
xinput list-props "Aiptek"
```

This gives:
> Device 'Aiptek':
    Device Enabled (135):    1
    Coordinate Transformation Matrix (137):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (258):    0
    Device Accel Constant Deceleration (259):    1.000000
    Device Accel Adaptive Deceleration (260):    1.000000
    Device Accel Velocity Scaling (261):    10.000000

I had thought the problem was that once I press down it doesn't register the pen being lifted. However, in reality as soon as I place the pen near the tablet, even without putting any pressure on the nib, it immediately registers light pressure. So in gimp, without having used the pen at all for anything else, one I hold the pen above the tablet it starts producing a faint grey paint, then pressing down produces darker shades. From that point on, however, ubuntu accepts no other left mouse clicks from any other mouse plugged in until I unplug the tablet. Hence why I am interested in seeing if changing the device of the pointer used by xorg might fix things.

I did try changing to a multipointer setup, so the pen tablet acts as a separate pointer to my system mouse (using xinput create-master ... etc.) but still the same problems with continuous light pressure being registered and other clicks then not working.

---

### Post by DrPotoroo on 2012-11-05
Well, turns out neither software nor hardware (sort of) are to blame for this. I decided to try a spare pen I had and, voila! Everything worked perfectly. So then, on a whim, I decided to try a different battery in the pen that was giving me trouble. I switched from the freshly charged NiMH battery I had been using to a non-rechargable zinc carbon battery and - what do you know? Both pens now work perfectly.

So - looks like pens might be prone to playing up when the voltage isn't high enough.

Since this is working, I'll just clarify the steps I used for the sake of others (they differ slightly from the wiki):

```
sudo apt-get install  xserver-xorg-input-aiptek
sudo gedit /lib/udev/rules.d/69-xserver-xorg-input-aiptek.rules
```

Paste the following in the editor, then save and close:
```
ACTION!="add|change", GOTO="xorg_aiptek_end"
KERNEL!="event[0-9]*", GOTO="xorg_aiptek_end"

ATTRS{idVendor}=="08ca", ENV{x11_driver}="aiptek", SYMLINK+="input/aiptektablet"

LABEL="xorg_aiptek_end"
```

Now to create the xorg configuration - this is the part that differs from the wiki, because the number in front of the filename needs to be HIGHER than the XX--evdev.conf, otherwise the tablet ends up being controlled by the evdev driver instead of the aiptek driver:

```
sudo gedit /usr/share/X11/xorg.conf.d/20-aiptek.conf
```

Now paste the following into this file, save and close:
```
Section "InputClass"
        Identifier "pen"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "SendCoreEvents" "true"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "1023" #Or might be 511, depending on your tablet's levels of pressure sensitivity
        Option "KeepShape" "on"
EndSection
```

Reboot. You could try restarting udev and X to save rebooting but that caused some strange behaviour on my system.

---

