---
title: "Bluetooth intellimouse stopped working after upgrade"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by amasidlover on 2006-01-13
Hi,

I've just done a dist-upgrade from Hoary to Breezy and although the boot screen is nicer and its sorted out my menus and various other nice bits, I have a couple of issues number 1 being my microsoft bluetooth intellimouse explorer has stopped working.

Under Hoary I had a very simple xorg.conf which had Buttons = 9 and ZAxisMapping = " 4 5", protocol = "ExplorerPS/2" , device = "/dev/input/mice". This config scrolled and went back and forward on the side buttons with no xmodmap or imwheel.

Under breezy the mouse no longer scrolls, in fact xev shows that only the normal buttons (1 2 3) are having their events captured. There are a lot of posts on here about using evdev - which would be fine, however my mouse is not showing properly in proc/bus/input/devices:
```

I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
H: Handlers=mouse0 event1 ts0
B: EV=b
B: KEY=6420 0 670000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio3/input0
H: Handlers=mouse1 event2 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0005 Vendor=045e Product=0098 Version=0010
N: Name=""
P: Phys=
H: Handlers=mouse2 event4 ts2
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

```

Now presumabley one of these is the bluetooth mouse - however if I use the Name and Phys of the Generic mouse, then nothing happens - in fact its suspicious that it shows on the same bus as the touch pad.

I've tried going back to my previous kernel, but that makes no difference so I'm guessing that it must be in the udev configuration.

I'm posting the relevant dmesg extract as well - but I'm not sure it tells us much:

```
[4294701.861000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x926eb1, caps: 0x804719/0x0
[4294701.864000] input: SynPS/2 Synaptics TouchPad on isa0060/serio2
[4294702.109000] psmouse.c: Failed to reset mouse on isa0060/serio3
[4294702.176000] ts: Compaq touchscreen protocol output
[4294704.505000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com[4294709.722000] input: PS/2 Generic Mouse on isa0060/serio3
[4294710.722000] psmouse.c: Failed to enable mouse on isa0060/serio3

```

I would really, really appreciate some help with this as I can't put up without having a scroll wheel for long and don't fancy having to do a total reinstall...

Thanks in advance!

Alex

---

### Post by amasidlover on 2006-01-13
Another check reveals that the entry with no Phys or Name is the Bluetooth mouse. Also hcidump shows no events associated with the wheel or side buttons.

I still suspect that this is a hotplug/udev issue - I'd be really interested to hear if someone does have this working even if I just know that it would be worth doing a complete reinstall, as I have a feeling that upgrading rather than clean install may be an issue here.

---

### Post by amasidlover on 2006-01-13
It looks like I sent my self up a blind alley when I tried the previous kernel version as it turns out that I had swapped the ZAxisMapping before doing it... However as a last ditch attempt I tried 2.6.10 from Hoary again and it worked with the correct ZAxisMapping.

It looks like there is a bluez-utils patch which should be applied to the kernel which for some reason hasn't been applied which enables the extra events.

I would try building my own kernel, but I can only find the patch for 2.6.14 on the bluez website. Not to mention that for some bizarre reason distros never include the .config that the main kernel was built with so that users can reproduce it on patched kernels - and from experience it is a real pain to try and get a kernel working which supports all the necessary features for the rest of the distro to work.

Anyway, I'm going to report this on bugzilla now...

---

