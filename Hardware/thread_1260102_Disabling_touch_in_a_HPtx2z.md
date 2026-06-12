---
title: "Disabling touch in a HPtx2z"
date: 2009-09-07
forum: Hardware
---

### Post by Aaron Issac on 2009-09-07
Hi ppl, I'm new to ubuntu and just made the switch from vista.

I followed all the threads and tutorials and finally got my tablet pen and touch working well.

But now i want to disable the touch only. I can disable the touch, but i notice that the cursor jerks or flickers when i put my fingers on the screen. This is very annoying, because when i draw, i tend to rest my palm on the screen.

I disable the touch with this command: xsetwacom set touch Touch off
or by editing the xorg.conf.
The touch is disable, but it still does interfere when i put my fingers on the screen or tap the screen lightly.

Is there a way to completely turn it of, or remove touch, so it will not interfere at all?

Thx alot for the help ppl!

---

### Post by Aaron Issac on 2009-09-07
Hi guys, I tried commenting out the 

#	Option		"Touch"		"on"


In the "touch" section of xorg.conf.

That does disable the touch, BUT

When i use the stylus and tap the screen with my fingers lightly the mouse tends to jerk or suddenly move to the edge of the screen really quick and comes back.

Seems it's still reading the touch, but this happens only when i have the stylus on the screen. When i dont have the stylus on the screen, it does not detect my touch at all no matter how hard i press.

Is there a way to disable the touch completely so it doesn't interfere?

---

### Post by Favux on 2009-09-07
Hi Aaron Issac,

I'm not sure why that's happening.  Did you disable the n-trig section in the 10-wacom.fdi like this HOW TO asks you to?:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

---

### Post by Aaron Issac on 2009-09-07
Hi Favux thx for the reply,

Yes i disabled the n-trig section.

I think i got it to work,

I put the "touch" block of code

```
Section "InputDevice"
    Identifier    "touch"
    Driver        "wacom"
#   The by-path below is for the HP TX2z with Vista firmware
    Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT & XT2 with Vista firmware
#    Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
    Option        "Type"        "touch"
    Option        "USB"        "on"
#    Option        "Touch"        "on"
    Option        "TopX"        "0"
    Option        "TopY"        "0"
    Option        "BottomX"    "9600"
    Option        "BottomY"    "7200"
EndSection
```

above the stylus block of code

```
Section "InputDevice"
    Identifier    "stylus"
    Driver        "wacom"
#   The by-path below is for the HP TX2z with Vista firmware
    Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT & XT2 with Vista firmware
#    Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
    Option        "Type"        "stylus"
    Option        "USB"        "on"
    Option        "Button2"    "3"    # make stylus button R mouse click
EndSection
```

in the xorg.conf.

RIght now that seems to work correctly.

---

### Post by Favux on 2009-09-07
Hi Aaron Issac,

That's very interesting.  Thanks for sharing that.  We did seem to note some "postition" dependence like that when we first started working with Rafi Rubin's xorg.conf Wacom sections.  I guess I thought we had eliminated that.  So that's a good tip.

Was that happening with one graphics program or more?  Was it Gimp?

---

### Post by Aaron Issac on 2009-09-08
hi Favux,
i think the problem is still there, my method did improve it a little bit though.

It happens anytime i have my stylus and fingers on the screen. In any program, the cursor jumps around wildly.

It happens when i tap the screen lightly, the cursor jumps.

Its probably a little annoying for the average user. But because i work with Zbrush alot, precision is very important to me, and a little jump can be very destructive!

---

### Post by Aaron Issac on 2009-09-08
After turning on the touch, i notice the  interference is still there.
The touch and pen is almost useless because of this.
If my palm or fingers rest on the screen the cursors jumps wildly even though im using the stylus!

The touch and stylus do work, but they seem to interfere with one another. Any reasons as to why?

---

### Post by Aaron Issac on 2009-09-09
still cant find any solution unfortunately.

Right now im using a piece of cloth to rest my palm on so the digitizer does'nt detect my hands..:(

---

### Post by Favux on 2009-09-09
Hi Aaron Issac,

Well one thing to keep in mind is that unlike with other tablets n-trig sends it's touch and stylus events on the same usb pci by-path, in other words the same input event.  Other tablets with touch use two seperate by-paths.  One for stylus/eraser and one for touch.

I don't know what's going on.  I don't think anyone else is reporting this.  All I can come up with is maybe you should try re-downloading and reinstalling the kernel deb and rebooting.

If that doesn't work try posting here:  [http://ubuntuforums.org/showthread.php?t=1038898](http://ubuntuforums.org/showthread.php?t=1038898)  and see if Ayuthia or someone can help you.

---

### Post by Ayuthia on 2009-09-09
The patch that I provided for the most recent kernel eliminates a lot of the palm touches with the pen is in use, but it does not eliminate it completely.  Currently the best way to get it separated is to go with the Windows 7 firmware.

---

### Post by Aaron Issac on 2009-09-13
Hi Ayuthia,

does that mean i have to find and install the N-trig windows 7 firmwear?
Will it still work on windows vista?

---

