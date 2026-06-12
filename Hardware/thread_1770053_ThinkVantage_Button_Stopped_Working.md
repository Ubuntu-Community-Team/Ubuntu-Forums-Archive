---
title: "ThinkVantage Button Stopped Working"
date: 2011-05-28
forum: Hardware
---

### Post by wolke on 2011-05-28
I have a Lenovo ThinkPad W520. The ThinkVantage button worked perfectly fine. xev gave it the sym XF86_Launch1, which I bound to gnome-terminal.

I installed the proprietary nvidia driver for the quatro 1000 it came with, and the thinkvantage button wouldnt work on boot. xev doesnt appear to receive it at all. Volume up/down/mute all work fine. The microphone mute button also stopped working {it reported something or other in xev and now nothing}.

Im gonna reboot with integrated gfx and see what happens.

>sudo /lib/udev/keymap /dev/input/by-path/platform-thinkpad_acpi-event
### evdev 1.0.1., driver 'ThinkPad Extra Buttons'
0x000 fn_f1
0x001 screenlock
0x002 battery
0x003 sleep
0x004 wlan
0x005 camera
0x006 switchvideomode
0x007 f21
0x008 f24
0x009 fn_f10
0x00a fn_f11
0x00b suspend
0x00c unknown
0x00d unknown
0x00e unknown
0x00f brightnessup
0x010 brightnessdown
0x011 kbdillumtoggle
0x012 unknown
0x013 zoom
0x014 volumeup
0x015 volumedown
0x016 mute
0x017 prog1
0x018 unknown
0x019 unknown
0x01a unknown
0x01b unknown
0x01c unknown
0x01d unknown
0x01e unknown
0x01f unknown

---

### Post by wolke on 2011-05-28
booting with integrated graphics enabled in bios completely fixes the issue. so, the nvidia driver appears to be causing the issue. WEIRD, i want my terminal button baaaack.

---

### Post by wolke on 2011-05-28
and no brightness control either! again, with integrated graphics selected, brightness works like a charm.

---

### Post by Tos_Phoenix on 2011-09-14
Has anyone resolved this issue?

I'm facing the same problem with kubuntu 11.10 on a Thinkpad T410.

---

### Post by hellfire_bg on 2011-10-30
I have the same issue with Thinkpad T61 and the NVidai proprietary drivers. With the NVidia drivers enabled all function key and special buttons work except the thinkvantage button. With the nouveau driver the thinkvantage button works. I think that this is a relatively old issue. For me the problem first appeared with the 260.x.x series of drivers but i never bothered to find a solution.

EDIT:

I have found a bug report for the issue - [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=613534](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=613534)

---

