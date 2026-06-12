---
title: "Touchscreen clicks before moving"
date: 2010-05-13
forum: Hardware
---

### Post by wxs on 2010-05-13
Hi,

I have an msi wind top ae1900, which is a touchscreen desktop running Ubuntu Lynx 10.04. The touchscreen worked out of the box using the evdev drivers (calibrating it was a whole other story, but let's not get into that here).

The issue I'm having is that the device often notices a click before it notices a move; that is, if I have the mouse positioned over a button, and then press *elsewhere* on the screen the button will often be pressed anyway. In fact sometimes only a click is noticed.

In case it helps, here is the output from xinput:
```

supportaler@Supportal1:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                	id=8	[slave  pointer  (2)]
&#9116;   &#8627; IDEACO  IDC 6681                       	id=9	[slave  pointer  (2)]
&#9116;   &#8627; IDEACO  IDC 6681                       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                     	id=11	[slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                     	id=12	[slave  keyboard (3)]
    &#8627; BisonCam, NB Pro                        	id=13	[slave  keyboard (3)]
supportaler@Supportal1:~$ 

```
the device in question is the one with id=9. I have verified with the command ```
xinput test 9
``` that that device is in fact often reporting clicks before moves.

Anyway, this may be a hardware issue, but I don't recall seeing this issue on the stock XP install that this machine came preloaded with.

Thanks in advance for any advice!

---

### Post by wxs on 2010-05-14
While I was trying to fix this I restarted X several times. One of these times, the problem was gone! I checked, and it turned out that that time the touchscreen had been configured as a pointer and not as a tablet.

Note in the output above from **xinput list** there are two entries for an IDEACO tablet. The first entry (id=9) is the one that was configured as a tablet and the second (id=10) is the one that was configured as a pointer. Unfortunately every time I boot now, no events show up in that second device, they all come from the first.

I've tried removing the rules that match tablets, so that only pointers get matched, but then the touchscreen stops working. It seems like almost every time I boot the pointer device for the touchscreen doesn't get any events (/dev/input/event6), and only its tablet device does (/dev/input/event4). What bothers me is this fact that every once in a while it suddenly works.

Any ideas?

EDIT: Here are the relevant lines of my Xorg.0.log file:
```

(II) config/udev: Adding input device IDEACO  IDC 6681 (/dev/input/event5)
(**) IDEACO  IDC 6681: Applying InputClass "evdev tablet catchall"
(**) IDEACO  IDC 6681: always reports core events
(**) IDEACO  IDC 6681: Device: "/dev/input/event5"
(II) IDEACO  IDC 6681: Found 3 mouse buttons
(II) IDEACO  IDC 6681: Found absolute axes
(II) IDEACO  IDC 6681: Found x and y absolute axes
(II) IDEACO  IDC 6681: Found absolute tablet.
(II) IDEACO  IDC 6681: Configuring as tablet
(**) Option "Emulate3Buttons" "True"
(II) IDEACO  IDC 6681: Forcing middle mouse button emulation on.
(**) Option "Emulate3Timeout" "50"
(**) IDEACO  IDC 6681: YAxisMapping: buttons 4 and 5
(**) IDEACO  IDC 6681: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "IDEACO  IDC 6681" (type: TABLET)
(II) IDEACO  IDC 6681: initialized for absolute axes.
(II) config/udev: Adding input device IDEACO  IDC 6681 (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device IDEACO  IDC 6681 (/dev/input/event6)
(**) IDEACO  IDC 6681: Applying InputClass "evdev pointer catchall"
(**) IDEACO  IDC 6681: always reports core events
(**) IDEACO  IDC 6681: Device: "/dev/input/event6"
(II) IDEACO  IDC 6681: Found 3 mouse buttons
(II) IDEACO  IDC 6681: Found absolute axes
(II) IDEACO  IDC 6681: Found x and y absolute axes
(II) IDEACO  IDC 6681: Configuring as mouse
(**) IDEACO  IDC 6681: YAxisMapping: buttons 4 and 5
(**) IDEACO  IDC 6681: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "IDEACO  IDC 6681" (type: MOUSE)
(II) IDEACO  IDC 6681: initialized for absolute axes.

```

---

### Post by charasoverride on 2010-05-22
Hello, I have the same problem, any solution yet?

---

### Post by chrae on 2010-05-26
I had the same issue.  The fix is to edit the file
```
/usr/lib/X11/xorg.conf.d/05-evdev.conf
```

Add the following section to the top of the configuration file:

```

Section "InputClass"
        Identifier "IDEACO Touchscreen"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evtouch"
        Option "reportingmode" "raw"
        Option "taptimer" "50"
        Option "longtouchtimer" "30"
        Option "maxx" "870"
        Option "maxy" "1230"
        Option "minx" "7280"
        Option "miny" "7100"
        Option "GrabDevice" "True"
        Option "Emulate3Buttons" "False"
        Option "SendDragEvents" "False"
EndSection

```

Values for maxx, maxy, minx, and miny will vary.

---

