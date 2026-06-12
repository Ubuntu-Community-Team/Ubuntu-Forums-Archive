---
title: "Mouse acting funny--can you help me diagnose?"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2008-04-14
Since the upgrade to hardy, my mouse has been behaving strangely, and I'm trying to determine if the problem is my laptop, my mouse, or hardy, so I can fix the issue or send the laptop in for repairs.

I have a Dell Vostro 1400, and the mouse in question is a logitech V200

Here's what happens. Some times when I click & drag with the mouse, even though I don't release the mouse button, the computer behaves as though I released it and then re-clicked. So, for instance, if I was selecting a large block of text, then the beginning mark would move to where the mouse freaked out and the selection would continue from then forward.

I'm not sure if the onboard touchpad is causing the problem, or if it is the mouse, the USB, or Ubuntu causing the issue. As of now, I have not been able to duplicate the problem reliably, but if I click the touchpad mouse while dragging with the other one, the behavior is very similar.

Is there anywhere I might look for errors, or anything I can do to help diagnose the problem? I've tried dmesg, kern.log, and the xorg logs in /var/log, but haven't found anything suspicious. Thanks.

---

### Post by xeth_delta on 2008-04-14
If you have a Gutsy Gibbon CD, boot from it, do not install anything or install over, just try the trackpad. If the problem is not present there, it is obvious it's a configuration problem on your current Ubuntu installation.

Please take into account that 8.04 is still Beta and as such might still have teething problems. The official stable release won't happen for another week, at least.

---

### Post by enigma_0Z on 2008-04-14
well I'm not sure if it's an issue w/ hardy or my hardware--I don't think the problem started immediately after hardy was installed.

is there something else I can do in the meantime? Cd's take a long time to download.

---

### Post by xeth_delta on 2008-04-14
> **enigma_0Z said:**
> well I'm not sure if it's an issue w/ hardy or my hardware--I don't think the problem started immediately after hardy was installed.

is there something else I can do in the meantime? Cd's take a long time to download.

We could try to look at what options are placed in "/etc/X11/xorg.conf". Post its contents between CODE tags. Did you make any mouse configuration changes since installation?

---

### Post by enigma_0Z on 2008-04-16
Actually... I think the mouse was dying.. other mice didn't have any issues, and I just bought one which is similar (Logitech VX Nano) and it has no issues...

I have tried every combination of mouse driver only, evdev, auto-dev, evdev protocol, etc. and nothing worked... As far as I can tell, it was a hardware issue. Sorry for wasting anyone's time. I should have known better anyways... most software problems aren't so intermittent.

But, here's the relevant sections...

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "CorePointer"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "V200"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
    Option         "Name" "Logitech USB Receiver"
    Option         "SendCoreEvents"
    Option         "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "SendCoreEvents" "true"
    Option         "topedge" "175"
    Option         "bottomedge" "660"
    Option         "leftedge" "125"
    Option         "rightedge" "925"
    Option         "LTButton" "3"
    Option         "RTButton" "2"
    Option         "FastTaps" "True"
EndSection
```

And I'm using btnx now for the extra buttons (tilt wheel) on this new mouse. Thanks, and sorry again.

---

### Post by xeth_delta on 2008-04-16
Don't worry about it. Good to know it's working properly now. Many times hardware issues are the last ones we check. :)

Please remember to mark the thread as solved.

---

