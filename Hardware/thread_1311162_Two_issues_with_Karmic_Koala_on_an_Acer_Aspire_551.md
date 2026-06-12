---
title: "Two issues with Karmic Koala on an Acer Aspire 5516"
date: 2009-11-02
forum: Hardware
---

### Post by logic11 on 2009-11-02
I have an Acer Aspire 5116 which worked perfectly on Ubuntu 9.04, but since I upgraded I don't have my touchpad (I have a mouse so not that big a deal) and it won't activate my broadcom wireless sta adapter (even though it reports it as being present) so my wireless doesn't work at all. If I can't get these two issues dealt with I will have to downgrade to Jaunty (not the worst think in the world, but Karmic Koala is just so nice).

Please help...

---

### Post by oooh on 2009-12-06
Hi there !

The touchpad thing may be caused by the new xorg policy in karmic. 

Did you check the /etc/X11/xorg file? Karmic comments out a lot of lines there as it delegates the I/O control to HAL now.

So maybe you need to start looking at HAL to try to make touchpad run again.

Try this: tpconfig, it will tell you if the touchpad is there.
cat /proc/bus/input/devices will tell you if there are touchpad devices in there
dmesg | egrep -i 'input|touch|track' as well.

Good luck !

---

### Post by oooh on 2009-12-06
Finally I got it working ! 

Check this out and try all possibilities, it must do the trick in a way or another.

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

(this is in case your touchpad is a Synaptics)

In my case I did this:

I added this section to the /etc/X11/xorg.conf:

Section "InputDevice"
    # generated from default
    Identifier     "Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Protocol" "auto-dev"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
EndSection

They key was the SHMConfig being ON.

After restart, the touchpad was working.
Hope that this helps!

By the way, another thing to check is:
synclient -l
Check the line TouchPapOff, if it is 1, then you know that the touchpad is FINE, it is just OFF. To set it ON, for me the trick was the above

Good luck !

---

