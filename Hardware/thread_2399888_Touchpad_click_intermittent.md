---
title: "Touchpad click intermittent"
date: 2018-08-30
forum: Hardware
---

### Post by tristan-wheelworks on 2018-08-30
I'm having an issue with the touchpad on a new Dell XPS 13 2-in-1 9365.  The physical "hard" click works every time, but the tap "soft" click is intermittent and more often that not does not register a click.

I've got the same issue under 18.04 and Fedora 28.  Windows has no similar problem.

Many XPS threads indicate there are two drivers competing for the touchpad and that disabling the synapics driver solves issues, however I'm unsure as to whether my system has both drivers running.
```

$ cat /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0007 Version=01a1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003

I: Bus=0018 Vendor=06cb Product=76af Version=0100
N: Name="DLL077A:01 06CB:76AF Touchpad"
P: Phys=i2c-DLL077A:01
S: Sysfs=/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-7/i2c-DLL077A:01/0018:06CB:76AF.0007/input/input17
U: Uniq=
H: Handlers=mouse3 event12 
B: PROP=5
B: EV=1b
B: KEY=e520 10000 0 0 0 0
B: ABS=260800000000003
B: MSC=20

(and also lists many more drivers)
```

but then the synapics doesn't show in xinput - should it?

```
$ xinput --list&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:15                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:15                id=7    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-touch:15                           id=9    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-stylus:15                          id=10    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-eraser:15                          id=11    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-cursor:15                          id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]     &#8627; xwayland-keyboard:15 id=8    [slave keyboard (3)]


```

There is also no "[COLOR=#545454][FONT=arial]50-synaptics.conf" which many posts indicate to.[/FONT][/COLOR]

```

$ ls /usr/share/X11/xorg.conf.d
10-evdev.conf   
10-radeon.conf    
70-wacom.conf
10-quirks.conf  
40-libinput.conf  
71-libinput-overrides-wacom.conf

```

Am I running two drivers?  If so how do I disable one?

If I'm not running two drivers any ideas what is causing the intermittent touch?

Thanks!

---

