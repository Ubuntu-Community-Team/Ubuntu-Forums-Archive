---
title: "tips sorting out intel 915 &amp; external monitor?"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by jslag on 2007-04-21
I'm trying to get an external monitor working with my HP DV1000, but not having any luck.

The video chipset is an intel 915GM; the monitor is an Acer AL2051W that supports 1680x1050.

First thing I tried is the 915resolution program. After adding 1680x1050 to /etc/defaults/915resolution, I get
```
915resolution -l:
. . .
Mode 6f : 1680x1050, 8 bits/pixel
Mode 70 : 1680x1050, 16 bits/pixel
Mode 71 : 1680x1050, 32 bits/pixel
```

Then I added the resolution to xorg.conf:
```
  SubSection "Display"
    Depth   24
    Modes   "1680x1050" "1280x768" "1024x768" "800x600" "640x480"
  EndSubSection
```

However, after restarting GDM, 1680x1050 still doesn't show up in the Screen Resolution dialog.  Am I missing a step? Anything I should be looking for in the X log to track down what's going on? 

As an aside, I tried replacing the i810 driver with the one in xserver-xorg-video-intel, but it was a total failure. On the plus side, 1680x1050 did appear under Screen Resolution. On the downside, that resolution didn't work correctly: only part of the desktop appeared, and the onscreen menu indicated that the monitor thought it was running 1280x1024. Additionally, both the external and laptop screens stayed on all the time (the toggle between modes wasn't working) and the laptop's native resolution of 1280x768 wasn't available any more.

---

### Post by jslag on 2007-04-21
On further inspection, 915resolution and X don't seem to be agreeing:


```
$ sudo 915resolution -l
(...)
Mode 6f : 1680x1050, 8 bits/pixel
Mode 70 : 1680x1050, 16 bits/pixel
Mode 71 : 1680x1050, 24 bits/pixel
```

(updated from 32 to 24 bits, per various mailing list posts)

however, /var/log/Xorg.0.log includes the following, suggesting that X isn't wise to the mode. Can anyone confirm if I'm reading these right? If so, why wouldn't X be picking up the mode?

```
Mode: 71 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
. . . 
(II) I810(0): Not using mode "1680x1050" (no mode of this name)
```

---

### Post by jslag on 2007-05-03
Progress. I noticed that, while there doesn't seem to be anything in the 915resolution docs that would give you reason to think one mode is different than the others, doing the same thing only using mode 38 actually worked. 
```
sudo 915resolution 38 1680 1050
```
After doing that, running dpkg-reconfigure xserver-xorg made the 1680x1050 resolution available. 

Still having problems of a weird mode being used, which has the effect of the monitor claiming that it's running at 1680x1050 but not displaying all of the screen - maybe 50 to 100 pixels are missing on the right-hand side.

---

### Post by jjordan on 2007-05-03
It is best to use a mode that is not being used.  

The mode change you make is NOT persistent, you must run it each time you boot. There is an init script you can edit to make this happen automatically when you boot.

I am using a Fujitsu P1510 with a 1024 X 600 screen and an i915 video "card" with a Viewsonic monitor at 1680 X 1050 in a twinview setup.  Works great except I can only get DRI on the laptop screen.

-j

---

### Post by jslag on 2007-05-04
> **jjordan said:**
> It is best to use a mode that is not being used.  

That's why I picked 6f - there was no resolution set, much less being used.

Now I'm wondering if "not being used" means, already set to some value that you don't intend to use, as opposed to not set to a value at all.

---

