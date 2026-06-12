---
title: "Asus Laptop - Intel chipset - Fn Keys inc Brightness non-functional"
date: 2015-07-12
forum: Hardware
---

### Post by TBerk on 2015-07-12
[ edited in line w/ recent developments... ]

OK, so I've been searching a bit and it seems no one has a good handle on 

1) Activating the Fn (Function) Keys default effect(s)  and/or

2) Enabling Brightness control of the laptop's backlighting.

In my particular case I am running an Asus x551m w/ a dual boot of the factory Win8.1 and Ubuntu Studio (<-- = XFCE) v14.04.
I selected 'All Variants' because I don't think this is limited to XFCE based versions.

Following in the footsteps of others I've tried a few things so far:

```
ls /sys/class/backlight/
**intel_backlight**


```

```
sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf
sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf

``` Where I pasted and saved:
> Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
and rebooted.   Didn't seem to make any effective change.

Besides the Brightness, there are other functions I would also like to enable, such as 

(Note: holding the 'Fn' key down while testing these keys found *some* were actually working...)

- F1 . Sleep (**Partial** Offers up the 'Log Off' screen where I can choose 'Suspend'.)
- F2 . Wifi Radio Off/On
- F5/6 . Brightness
- F7 . (it has an 'x' which I forget but think is 'blank screen'...) (**Works** Dims screen, turns Off backlighting.)
- F8 . Internal/External Video toggle (**Partial** Brings up the 'Display' applet. rather it toggled 'Internal/External/Both' instead)
- F9 . Trackpad disable (**Works**)
- F10/11/12 . Volume Control (**Works** Huzaah!, at some point this wasn't working, but is now. ???)

This last is likely the second priority on the list; being able to mute or adjust the Volume with just a key-press would be very useful*, as would brightness control of the screen.

*(Audio controls unexplainable working now.)

(And while I'm at it, I'm going to throw in better support of enabling 'Sleep' mode, esp when the lid is closed. Right now the only option I have when the lid is closed is to 'blank the screen'...)

In closing, I'm hoping there might be some answer that opens the door to better Intel chipset (Graphics, Sound, Power management) support on this laptop. 

In the mean time I'm continuing to archive dive this forum and others and will report back. (The Compatible Hardware sticky alone is 22 pages deep and counting...)

---

