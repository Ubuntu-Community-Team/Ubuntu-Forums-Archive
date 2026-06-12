---
title: "To HAL or not to HAL, that is the question."
date: 2009-03-07
forum: Hardware
---

### Post by mavrick13927 on 2009-03-07
I have been trying to configure my Logitech M-BJ58 USB mouse.  I have done much reading on the web, and am getting conflicting info.  Does 8.04 support HAL or not?  If it does, what am I supposed to name the policy file I place in the /etc/hal/fdi/policy directory?  Currently I have my xorg.conf like this:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


Section "InputDevice"

	# generated from default
    Identifier     "Mouse0"
    Driver         "evdev"
    #Option         "CorePointer"
    #Option         "Protocol" "auto"
    #Option         "Device" "/dev/psaux"
    Option         "Device" "/dev/input/by-id/usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse"
    #Option         "Emulate3Buttons" "no"
    #Option         "ZAxisMapping" "4 5"
EndSection
```


My fdi file for the mouse looks like this:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <merge key="input.x11_options.Emulate3Buttons" type="string">no</merge>
        <merge key="input.x11_options.ZAxisMapping" type="integer">4 5</merge>
    </match>
  </device>
</deviceinfo>
```

Also, if 8.04 supports HAL, do I change the driver in xorg.conf, or in the fdi file?

I am running Kubuntu 8.04 LTS on an Acer Aspire T160 with an added nVidia GeForce 6600 LE video card.  I have both monitors setup using Xinerama. To my knowledge I am not running Compiz.  The mouse mostly works with the fdi file named mouse.fdi.  It seems to have a mind of its own in full screen games though.

Thanks in advance for any help you can provide to get my mouse working with or without HAL.

---

