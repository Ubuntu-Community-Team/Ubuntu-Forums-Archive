---
title: "Synaptics trackpad"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by mellon85 on 2006-06-14
I can't manage to setup the synaptics trackpad with qsynaptics. It always returns 

```

Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?

```

even if I have enabled it in xorg.conf with

```

Option          "SHMConfig"             "1"

```

---

### Post by TwiceOver on 2006-06-14
Try:

SHMConfig "on"

Instead of 1 or 0.  This is how it is in my setup and qsynaptics works great.  You should also have synclient installed.  You can use that to view your current settings and change them on the fly to tweak your touchpad just right.  I ended up using synclient rather than qsynaptics.

---

### Post by mellon85 on 2006-06-14
I tried to set SHMConfig to on, but nothing changed :(

```

synclient -h
Can't access shared memory area. SHMConfig disabled?

```

---

### Post by Lunar_Lamp on 2006-06-15
My working synaptics touchpad in xorg.conf is like this:

```
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "SHMConfig" "on"
EndSection

```

It was actually working with SHMConfig set to off (or not there, I don't remember) - but I added it so that I could toggle it's state on/off.  You will need to restart X to see the effects of any changes to you xorg.conf though (sorry if you already tried this, but it;s easy to forget this kind of thing sometimes)!

---

### Post by mellon85 on 2006-06-15
mine is

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

```

not very funny...
I have restarted Xorg. It's not a matter to repeat it, there are so many newbies out there.
I have read that installing the xfree86 driver and substitute it to the xorg driver would have fixed the problem, but it doesn't work too.
Is it possible that my trackpad doesn't support this? Can't i verify it?

---

### Post by mellon85 on 2006-06-15
I had some wacom device recognized by the installer. It is a known bug in launchpad.
I have removed them, but nothing changes...

---

### Post by marcog on 2006-06-17
I also get the same error, even with SHMConfig set to on.

---

### Post by jphofmann on 2006-06-20
It is very possible that your touchpad is not synaptics. Could be an alps as it was in my case.  The fix on [http://home.uchicago.edu/~chad/](http://home.uchicago.edu/~chad/) worked for me... Look under the heading "Disabling the tap-to-click "feature" on a laptop touchpad".

---

### Post by mellon85 on 2006-06-20
How can i detect if it's an alps?
Follwing this page in teh wiki doesn't help too
[https://wiki.ubuntu.com/SynapticsTouchpadHowTo?#head-d52222ac8869d4002190e57bb7198e2d5c5c42ac](https://wiki.ubuntu.com/SynapticsTouchpadHowTo?#head-d52222ac8869d4002190e57bb7198e2d5c5c42ac)
doing "cat /proc/bus/input/devices" produces this output
```

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=1241 Product=1166 Version=0200
N: Name="HID 1241:1166"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

```
but I have no clue on what is this :-p 
Now i have the usb mouse attacched too.

I can only see that it is not a Synaptics one (from /var/log/Xorg.0.log)

```

...
(II) Synaptics touchpad driver version 0.14.3
Synaptics Touchpad no synaptics event device found (checked 14 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "on"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
...

```

I am not having any tap-to-click problem (if it should be working it doesn't work).
As said in the pages you posted here, the patches for alpsa are already in the dapper kernel

---

### Post by ZeroXu on 2006-07-06
I thinks it is a bug in xorg's touchpad driver, so don't change any config in xorg.conf and try this:
#apt-get remove xorg-driver-synaptics
#apt-get install xfree86-driver-synaptics
#ln -sf /usr/X11R6/lib/modules/input/synaptics_drv.o /usr/lib/xorg/modules/input/synaptics_drv.o
#reboot

My laptop is ASUS M5N, after doing this, my 'Fn+F9' can switch on/off of my touchpad.

---

