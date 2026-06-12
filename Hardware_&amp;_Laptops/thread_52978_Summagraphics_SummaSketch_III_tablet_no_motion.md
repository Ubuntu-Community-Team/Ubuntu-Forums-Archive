---
title: "Summagraphics SummaSketch III tablet: no motion"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by thelusiv on 2005-07-29
I'm trying to set up a SummaSketch III tablet on one of my Ubuntu machines. I have the device plugged in and powered on, using the stylus (not the puck). It is attached to the first serial port, and if I cat /dev/ttyS0 I get some garbage on the terminal as I move the stylus and click, so I know the tablet works. I have attempted to set it up with X.org and so far I haven't had much luck. I found a few places around the web that described setting it up with XFree86, so I followed those, and came up with the following additions to my xorg.conf:

```

Section "Module"
...
        Load    "summa"
EndSection

...

Section "InputDevice"
        Identifier      "SummaSketch III"
        Driver          "summa"
        Option          "Device"                "/dev/ttyS0"
        Option          "Resolution"            "2540"
        Option          "MaxY"                  "12000"
        Option          "MaxX"                  "12000"
        Option          "Mode"                  "Absolute"
        Option          "Cursor"                "stylus"
        Option          "Compatible"
EndSection

...

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "SummaSketch III"
EndSection

```

And here's relevant the output from /var/log/Xorg.0.log:

```

xf86SumInit allocating...
xf86SumInit CollectInputOptions... done.
(**) SummaSketch III: serial device is /dev/ttyS0
(**) SummaSketch III: resolution given 2540
(**) SummaSketch III: set for absolute mode
(**) SummaSketch III: will not query firmware ID.
(**) SummaSketch III: cursor mode is cursor
(II) XINPUT: Adding extended input device "SummaSketch III" (type: SummaSketch Tablet)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "9600"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "Odd"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(==) SummaSketch III: tablet size is 6.45in. x 6.45in., 16383x16383 lines of resolution
(==) SummaSketch III: using tablet area 16383 by 16383, at res 2540 lpi
(==) SummaSketch III: Using increment value of 12
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

The effects of all this is that X.org seems happy with the tablet but when I move the stylus, nothing happens. Do I need to do something to enable the stylus?

**edit**: just noticed, it also says the tablet size is 6.45 x 6.45 in. - this is incorrect. It's about a foot by a foot, maybe bigger (haven't measured it). Is this changeable?

---

### Post by thelusiv on 2005-07-29
Alright! I have figured out the no motion problem, I needed to add a line to the InputDevice section that says:
```
 Option "AlwaysCore" "true" 
```
and that fixed it. Now, that 6.5x6.5 in. dimension is a limitation, only a square in the top-left corner works. I think I know how to fix it, will report back soon if I get it figured out.

---

### Post by thelusiv on 2005-07-29
Silly me, I started in the wrong place. I guess Google can sort of lead one astray...anyway I figured it all out, both my previous posts' settings were wrong. I fixed it however and it works great now. Here's my InputDevice section now:
```

Section "InputDevice"
        Identifier      "SummaSketch III"
        Driver          "summa"
        Option          "Device"                "/dev/ttyS0"
        Option          "Mode"                  "Absolute"
        Option          "Cursor"                "stylus"
        Option          "SendCoreEvents"        "true"
EndSection

```
and here's the X.org output:
```

xf86SumInit allocating...
xf86SumInit CollectInputOptions... done.
(**) Option "SendCoreEvents" "true"
(**) SummaSketch III: always reports core events
(**) SummaSketch III: serial device is /dev/ttyS0
(**) SummaSketch III: resolution given 1200
(**) SummaSketch III: set for absolute mode
(**) SummaSketch III: cursor mode is cursor
(II) XINPUT: Adding extended input device "SummaSketch III" (type: SummaSketch Tablet)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "9600"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "Odd"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(==) SummaSketch III firmware ID : MM III  12 x 12 Tablet  by Summagraphics  Firmware Version 1.91
(==) SummaSketch III: tablet size is 12.00in. x 12.00in., 6000x6000 lines of resolution
(==) SummaSketch III: using tablet area 6000 by 6000, at res 500 lpi
(==) SummaSketch III: Using increment value of 4
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```
Hope someone else benefits from this info. :) I got this tablet free from a client - when I visited to help her set up her web site, we started talking about tablets and she showed me the two 12x12 SummaSketch tablets they had, and told me I could take one since there are no Windows drivers for them anyway. It was a little dusty, but I cleaned it up - it is very large, sturdy, all around great piece of hardware. My only beef is the stylus - I wish the pen was clicky instead of just springy, and I wish that there wasn't a cable on the back of it.

Anyway, if you can get ahold of one of these things I highly recommend it! They are pretty old now so you can get them quite cheap. Windows XP support is nil, but Ubuntu does a great job with it. "But I can't fit a 12x12 tablet on my desk, where will my mouse go?" you say....well It also makes a great mousepad, for mechanical and optical...

---

### Post by el_itur on 2007-01-22
I have one of those, right here right now, I know this is an old topic, but, I still get this message ```

(II) LoadModule: "summa"
(WW) Warning, couldn't open module summa
(II) UnloadModule: "summa"
(EE) Failed to load module "summa" (module does not exist, 0)
(II) LoadModule: "summa"
(WW) Warning, couldn't open module summa
(II) UnloadModule: "summa"
(EE) Failed to load module "summa" (module does not exist, 0)

```
Is this module out of the newer kernel. 
I'm using edgy eft.

Thanks for any reply

---

### Post by tgrignon on 2007-12-09
Hi thelusiv,

I just hooked up a Dell Dimension 2400 machine and I saw your message about the Summasketch III.  I have one too but the serial connector is a 25 pin whereas the serial connector on the back of the Dell is 9 pins.  Any ideas?

---

### Post by laharrin on 2008-04-24
@tgrignon: I am wondering if you found a work-around for the serial port.  I have the 25 pin connected to a 9 pin adapter, but my computer has no serial input, so I have another adaptor to change 9 pin to USB.

---

