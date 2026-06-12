---
title: "Brightness controls too coarse"
date: 2014-01-10
forum: Hardware
---

### Post by Maximus559 on 2014-01-10
I just installed Xubuntu 13.10 64-bit on the machine in my signature. When I was running 12.10, I had to do some kind of hack in order to control screen brightness with the function keys. Even then, there was no on-screen display and brightness levels would reset after every suspend-resume cycle.

Now, with 13.10, brightness control works out of the box; however, the controls are too coarse (i.e., they skip steps). Because of this, I'm unable to dial in the right backlight setting for low-light environments.

Is there some way to adjust the granularity of the brightness controls? (Perhaps via xfce4-settings?) Alternatively, is there some application which would give me finer grain controls?

---

### Post by Toz on 2014-01-10
Can you post back some more info about your setup? Specifically:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video card(s):
```
lspci -k | grep -iA2 VGA
```

3. Info about your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by Maximus559 on 2014-01-11
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=1064532e-6947-4e2a-8cf8-0d8927cc8f04 ro persistent quiet splash vt.handoff=7

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1467
    Kernel driver in use: i915

/sys/class/backlight/acpi_video0
78
78
100
/sys/class/backlight/intel_backlight
3762
3762
4882
```

---

### Post by Toz on 2014-01-11
First try this:

1. Create a **/usr/share/X11/xorg.conf.d/20-intel.conf** file with root privileges (from a terminal window):
```

sudo -i mousepad /usr/share/X11/xorg.conf.d/20-intel.conf
```

2. Copy/paste the following code:
```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

3. Save the file.

4. Log out and back in again to test.

---

### Post by Maximus559 on 2014-01-12
Thank you, that has done it. The brightness level still jumps when I first hit one of the keys, but if I hold the key down, the brightness scales linearly. I'm able to dial in any brightness setting I like, so I consider this problem solved.

---

