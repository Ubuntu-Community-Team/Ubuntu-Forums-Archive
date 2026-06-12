---
title: "[Intrepid] Thinkpad middle button not working, even with .fdi"
date: 2008-12-03
forum: Hardware
---

### Post by walkeraj on 2008-12-03
Hello, I recently purchased a Thinkpad X41 and it's working very well so far.  Decided to install Intrepid on it and the only problem I have so far is that the middle mouse button does not work, nor do any of the fixes for it.

I looked into it and discovered that xorg is using HAL for device configuration now, so, following the solution offered [:here:]("http://psung.blogspot.com/2008/09/scrolling-with-thinkpads-trackpoint-in.html"), I created the file **/etc/hal/fdi/policy/mouse-wheel.fdi**:

```
<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>
```

Which, unfortunately, doesn't work.  If I attempt to switch the pointer, I receive the following:

```

$ xinput set-pointer "TPPS/2 IBM TrackPoint"
X Error of failed request:  BadDevice, invalid or uninitialized input device
 Major opcode of failed request:  146 (XInputExtension)
 Minor opcode of failed request:  12 (X_ChangePointerDevice)
 Serial number of failed request:  12
 Current serial number in output stream:  12

```

This is all very strange, because the logs look ok...

```

==from /var/log/Xorg.0.log===
(II) config/hal: Adding input device TPPS/2 IBM TrackPoint
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Configuring as mouse

```

And, more strangeness, there seem to be Macintosh mouse buttons present?

```

$ xinput list
"Virtual core keyboard" id=0    [XKeyboard]
       Num_keys is 248
       Min_keycode is 8
       Max_keycode is 255
"Virtual core pointer"  id=1    [XPointer]
       Num_buttons is 32
       Num_axes is 2
       Mode is Relative
       Motion_buffer is 256
       Axis 0 :
               Min_value is 0
               Max_value is -1
               Resolution is 0
       Axis 1 :
               Min_value is 0
               Max_value is -1
               Resolution is 0
"Macintosh mouse button emulation"      id=2    [XExtensionPointer]
       Num_buttons is 32
       Num_axes is 2
       Mode is Relative
       Motion_buffer is 256
       Axis 0 :
               Min_value is -1
               Max_value is -1
               Resolution is 1
       Axis 1 :
               Min_value is -1
               Max_value is -1
               Resolution is 1
"TPPS/2 IBM TrackPoint" id=3    [XExtensionPointer]
       Num_buttons is 32
       Num_axes is 2
       Mode is Relative
       Motion_buffer is 256
       Axis 0 :
               Min_value is -1
               Max_value is -1
               Resolution is 1
       Axis 1 :
               Min_value is -1
               Max_value is -1
               Resolution is 1
"AT Translated Set 2 keyboard"  id=4    [XExtensionKeyboard]
       Num_keys is 248
       Min_keycode is 8
       Max_keycode is 255
"Video Bus"     id=5    [XExtensionKeyboard]
       Num_keys is 248
       Min_keycode is 8
       Max_keycode is 255

```


Can anyone help me pin down what's going on here?

**Edit:** is this too new, do I need to submit a bug?

---

### Post by walkeraj on 2008-12-17
I'm going to bump this once and ask:

1) Has anyone else had this or a similar problem?
2) If not, do I need to submit a bug in Launchpad, with the HAL team, or with the Xorg team?

---

### Post by oldguy51 on 2009-01-12
I have an older IBM T23 and am experiencing the same issue since upgrading to 8.10 from 8.04.  It worked in 8.04 with xorg.confg change but lost scroll for stick with 8.10.

I also tried the .fdi file fix with no luck.  I have limited Ubuntu experience and did not check the logs as you did but I am still reading and looking for an answer.

---

