---
title: "Dell D620: connect to data projector?"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by howardcheng on 2006-06-14
I got a Dell D620 and I have just tried to plug it to an external data projector (1024x768).  I have wide screen (1440x900) and there seems to be a problem here.

  1. If I press Fn-F8 once, I get the 1440x900 screen displayed on the projector.
      The image is "compressed" but otherwise okay.  But my LCD screen is black.

  2. I press Fn-F8 again, this time both LCD and projector screens are on.  LCD
      is 1440x900 but now the projector screen shows only  a 1024x768 part of the
      screen (but in the "right aspect ratio").

  3. I can press Fn-F8 a few more times, at some point my LCD screen will get
      corrupted with some garbage at the top and everything else shifted down a
      bit.  Hitting Fn-F8 again hangs everything (keyboard wouldn't respond, not 
      even the caps lock light).  Maybe it is only the X server that hangs, but I have 
      no way to log on remotely to check.

Ideally, I would like to use 1440x900 on my LCD screen and then a "compressed" image of 1024x768 on the projector screen.  But I would be happy if I just use 1024x768 on both.  Can anyone help?  Thanks.

---

### Post by fast1 on 2006-06-14
Did you try to first set the resolution to 1024x768 and then press Fn-F8?

---

### Post by howardcheng on 2006-06-14
[QUOTE=fast1]Did you try to first set the resolution to 1024x768 and then press Fn-F8?[/QUOTE]

I cannot seem to do that.  I put "1024x768" into the modes of xorg.conf but the mode is not used and I cannot switch to it.   Here is what Xorg.0.log says:

```

(II) I810(0): Generic Monitor: Using hsync range of 51.43-56.84 kHz
(II) I810(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1440 -> 2048).(--) I810(0): Virtual size is 1440x900 (pitch 2048)
(**) I810(0): *Built-in mode "1440x900"
(--) I810(0): Display dimensions: (300, 190) mm
(--) I810(0): DPI set to (121, 120)

```

---

### Post by fast1 on 2006-06-14
I had a similar problem for the external monitor (I have a D620 too).
I solved it with 915resolution.
Use the option -l to see the available modes.
Pick one you don't need (for me it was mode 5a 1600x1200) and set it to the new resolution. For example, I wanted 1680x1050 and I typed

> 915resolution 5a 1680 1050

This allowed me to switch to both 1680x1050 or 1024x768.

---

### Post by howardcheng on 2006-06-14
[QUOTE=fast1]I had a similar problem for the external monitor (I have a D620 too).
I solved it with 915resolution.
Use the option -l to see the available modes.
Pick one you don't need (for me it was mode 5a 1600x1200) and set it to the new resolution. For example, I wanted 1680x1050 and I typed

> 915resolution 5a 1680 1050

This allowed me to switch to both 1680x1050 or 1024x768.[/QUOTE]

I do have the mode 1024x768 listed in "915resolution -l", but still can't switch to it.

---

### Post by valaraukar on 2006-08-17
The same trouble.
```
(WW) I810(0): config file hsync range 60-66.31kHz not within DDC hsync ranges.
(II) I810(0): Monitor0: Using hsync range of 60.00-66.31 kHz
(II) I810(0): Monitor0: Using vrefresh value of 60.00 Hz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1680 -> 2048).
(--) I810(0): Virtual size is 1680x1050 (pitch 2048)
(**) I810(0): *Built-in mode "1680x1050"
(--) I810(0): Display dimensions: (330, 210) mm
(--) I810(0): DPI set to (129, 127)
```
I need 1024x768 to play Quake 3 fullscreen, not "in the left bottom corner".
855resolution helped to get two more modes "recognized" as *Built-in. They are : 1400x1050 and 1280x1024. 
Why i can't get working 1024x768 is a mystery for me. I've even tried "Depth 16".

Oh i forgot to say. It's <censored> intel 915gm and its' <censord> "bios".

---

### Post by usererror on 2007-06-20
When I press FN+F8 on my keyboard, I don't get video to my external monitor.  I Have to reboot and then press FN+F8 while I'm at the Grub Screen or else I cannot get video to my external monitor.  Any ideas?

---

