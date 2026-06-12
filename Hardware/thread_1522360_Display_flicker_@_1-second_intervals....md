---
title: "Display flicker @ 1-second intervals..."
date: 2010-07-02
forum: Hardware
---

### Post by Moozillaaa on 2010-07-02
It's a new build, all new compatible stuff.

I thought it might be the video chip ATI Radeon 3300HD, on a [COLOR=Blue]FoxConn[/COLOR] board. So I bought another board - [COLOR=Red]BioStar[/COLOR] (with the same vid chip), and put the CPU and ram in, and fired it.

IT'S DOING THE SAME THING - FLICKER AT 1 SECOND INTERVALS!!! 30 - 40 times, then skips 10 seconds or so, and picks up again, at **PERFECT 1 second intervals**.

There is also an intermittent display problem - web pages do not 'finalize' the page load - the fonts stop loading in a large size. 'Refresh' the page finalizes font sizing to the smaller size...

:confused:

So is it the CPU? Or the ram?

CPU is Athlon II X3 440 3.0 Ghz.
Ram is Kingston KVR667K2D2 1G x 4 sticks.

Both are compatible with each board [COLOR=Blue]FoxConn[/COLOR] A7DA-S, and [COLOR=Red]BioStar[/COLOR] TA790GX.

The flicker is MOSTLY noticeable when the X-Screensaver GUI window is open:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160707&d=1276740208[/IMG]

---

### Post by Moozillaaa on 2010-07-02
bumpin' here...

---

### Post by cascade9 on 2010-07-03
Sounds more like a driver problem than anything to do with your RAM or CPU. 

Tried removing the ATI drivers, if you use them normally, or installing them if you dont?

---

### Post by Moozillaaa on 2010-09-09
These occasional display problems won't go away; does this mean anything to anybody?
> 
BUG: soft lockup - CPU#0 stuck for 11s! [Xorg:8184]This one I found in kern.log after X crashed (this is a once-weekly occurrence). Are there other places to look in "**log**" files for clues here on this display/driver(?) problem???



And this is from xorg.conf:

:
:
:

Section "Module"
    Load  "glx"
    Load  "dbe"
    Load  "v4l"
EndSection

:
:
:

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    VendorName  "ATI"
    BoardName   "ATI Radeon (vesa)"
    Option        "EnableMonitor" "crt1,tmds2i"
    BusID       "PCI:1:5:0"
EndSection

:
:
:

Anything look wrong here?

---

### Post by Moozillaaa on 2010-09-09
Ok - so I pulled the ATI accelerated graphics driver, and the associated modules removed themselves, and re-started. 

For the moment, I cannot re-create the geometric 'flicker' in GLSlideshow 'Preview' window, which was a createable error. That's fine so far..., I'll watch also for the X-crash too.

But at the moment, I haven't the option of increasing the screen resolution above 800 x 600...

---

### Post by Moozillaaa on 2010-09-11
The resolution choices are increased using the GUI for screen and graphics preferences (sudo displayconfig-gtk).

The flicker is gone from complex display (i. e.; display within display). The occasional X-crash has not re-occurred yet.

Solution is tentative for this machine. The second machine HTPC, also new build, same CPU and graphics chip, is feeding the same monitor, but also a SONY 32" TV, through the HDMI output. Will [COLOR=Blue]vesa -  Generic VESA-compliant video cards [/COLOR]driver support cloned output?

Anybody else using ATI HD 3300 graphics?

Thanks cascade...

---

