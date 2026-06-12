---
title: "touchpad problem: auto-dev not working properly!"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by cisforcojo on 2007-03-03
Hey all,

I have an ALPS touchpad and have been having a hell of a time trying to get tapping disabled!
Every time I reboot my computer, the device event of my touchpad changes. I am using:
/dev/psaux with the 'auto-dev' protocol but that always points to event 2. Somtimes it works. Most of the time it doesn't. Does anyone know what could be wrong?

/proc/bus/input/devices:
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse1 event4 ts1 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

Xorg.0.log:
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Alps Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "SHMConfig" "true"
(--) Setting defaults to alps values
(**) Option "LeftEdge" "120"
(**) Option "RightEdge" "830"
(**) Option "TopEdge" "120"
(**) Option "BottomEdge" "650"
(**) Option "FingerLow" "14"
(**) Option "FingerHigh" "15"
(**) Option "MaxTapTime" "0"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "20"
(**) Option "EdgeMotionMinZ" "30"
(**) Option "EdgeMotionMaxZ" "160"
(**) Option "EdgeMotionMinSpeed" "15"
(**) Option "EdgeMotionMaxSpeed" "15"
(**) Option "EdgeMotionUseAlways" "0"
(**) Option "UpDownScrolling" "1"
(**) Option "LeftRightScrolling" "0"
(**) Option "CircularScrolling" "0"
(**) Option "CircScrollTrigger" "0"
(--) Alps Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Alps Touchpad: always reports core events


GAH!
 
Any ideas? This is really throwing me for a loop. I also use a USB mouse but that is disconnected. I'm trying to get my computer working WITHOUT the usb mouse. Then I'll tackle that problem.

---

### Post by cisforcojo on 2007-03-06
-bump-

---

### Post by cisforcojo on 2007-03-13
bump?

---

### Post by spier on 2007-03-16
As far as I know, this behavior seems a (kinf of) bug in Edgy, as it works perfectly in Dapper.

That said, two workarounds:

- Ctrl+Alt+F1 then Ctrl+Alt+F7, somehow, reloads the xorg.conf settings;

- installing Syndaemon disables touchpad tappings while typing:
[ HowTo: Disable Synaptics Touchpad While Typing]("http://www.ubuntuforums.org/showthread.php?t=271052")

hth

---

### Post by cisforcojo on 2007-03-16
Yeah I've resigned myself to it being a bug. Not too much longer for Feisty!
I haven't been able to get any help on the matter. Even on the IRC channels no one has done 
much with disabling the touchpad. I've resigned myself to manually editing xorg.conf every time I bootup and restarting X.

---

### Post by Charles Hand on 2007-04-02
[http://www.ubuntuforums.org/showthread.php?p=2389724#post2389724](http://www.ubuntuforums.org/showthread.php?p=2389724#post2389724)

---

