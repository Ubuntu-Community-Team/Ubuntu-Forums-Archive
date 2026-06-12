---
title: "How do I calibrate my wacom device in Lucid?"
date: 2010-05-20
forum: Hardware
---

### Post by TygerFish on 2010-05-20
I'm using a Gateway M290/E295C tablet.  The Wacom device is detected by default with no issues.  But the automatic calibration is just awful.

In previous versions of Ubuntu, I've used xidump to track input values. I would use that information to put calibration settings in my xorg.conf file.  No problem then.

Now that I've moved to Lucid, I find that the package wacom-tools has been removed and that I cannot find a package containing xidump.  Is there a new method for calibrating Wacom pads?

---

### Post by Favux on 2010-05-20
Hi TygerFish,

The xsetwacom commands have been moved out of wacom-tools and moved to xf86-input-wacom for the Xserver 1.7 in Lucid.  So they are included by default.  Unfortunately wacomcpl is not available.

If you didn't save the coordinates from your previous xorg.conf you should be able to find them in Xorg.0.log in /var/log when the wacom driver initializes your devices.

You can then use xorg.conf options or a script file, call it say .xsetwacom.sh, with xsetwacom commands to apply calibration.

---

### Post by TygerFish on 2010-05-20
> **Favux said:**
> Hi TygerFish,

The xsetwacom commands have been moved out of wacom-tools and moved to xf86-input-wacom for the Xserver 1.7 in Lucid.  So they are included by default.  Unfortunately wacomcpl is not available.

If you didn't save the coordinates from your previous xorg.conf you should be able to find them in Xorg.0.log in /var/log when the wacom driver initializes your devices.

You can then use xorg.conf options or a script file, call it say .xsetwacom.sh, with xsetwacom commands to apply calibration.

Thanks for the answer!  I checked out the logfile:
```
$ cat /var/log/Xorg.0.log | grep "Serial Wacom Tablet:"
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(II) Serial Wacom Tablet: hotplugging dependent devices.
(II) Serial Wacom Tablet: hotplugging completed.
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=30730 bottom Y=18520 resol X=2540 resol Y=2540
```

That should at least give me a starting point where I can fiddle around with setting different values, but I still miss being able to see the values in real time to figure out where to set things... alas, laziness!  :)

---

### Post by TygerFish on 2010-05-22
Yep, that seems to have set me on the right track.  For other folks, this is how I calibrated it by hand (still more of a pain than the previous method.)

1) Find the device number of your tablet.
```
$ xsetwacom --list --verbose
... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device 'Power Button' (6).
... Found device 'Video Bus' (7).
... Found device 'Power Button' (8).
... Found device 'Sleep Button' (9).
... Found device 'AT Translated Set 2 keyboard' (10).
... Found device 'Serial Wacom Tablet eraser' (11).
Serial Wacom Tablet eraser ERASER    
... Found device 'Serial Wacom Tablet' (12).
Serial Wacom Tablet STYLUS    
... Found device 'Macintosh mouse button emulation' (13).
... Found device 'SynPS/2 Synaptics TouchPad' (14).
```
(from [http://ubuntuforums.org/showthread.php?t=1423278&page=1](http://ubuntuforums.org/showthread.php?t=1423278&page=1))

2) (as above) Find the default/current values for your system.
```
$ cat /var/log/Xorg.0.log | grep "Serial Wacom Tablet:"
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(II) Serial Wacom Tablet: hotplugging dependent devices.
(II) Serial Wacom Tablet: hotplugging completed.
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=30730 bottom Y=18520 resol X=2540 resol Y=2540
```

3) Tweak until you find good values.
```
$ xsetwacom set 12 TopX 60
```

4) Put the good values in your less /usr/lib/X11/xorg.conf.d/10-wacom.conf file.
```
Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
        Option "Button2" "3"
        Option "TopX" "60"
        Option "BottomX" "30690"
        Option "TopY" "10"
        Option "BottomY" "18350"
EndSection
```

---

