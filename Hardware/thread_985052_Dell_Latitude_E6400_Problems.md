---
title: "Dell Latitude E6400 Problems"
date: 2008-11-17
forum: Hardware
---

### Post by schneida on 2008-11-17
Hello!

I have some troubles with my Dell Latitude E6400 (with Intel Media Accelerator) running Ubuntu 8.10 x64. 
Hibernate and Standby don't work properly. They work sometimes, but most of the time the laptop simply hangs. Most of the time when I resume from Standby I see the mouse cursor, but can't move it.
Does anybody know how to fix that?

Another problem is the touchstick. It jumps when I try to move it and in the kernel.log is written:
```

psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 6
psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.
psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 6
psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.
psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 5
psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 6
psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 3
psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 3
psmouse.c: issuing reconnect request
input: DualPoint Stick as /devices/platform/i8042/serio1/input/input20
input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input21

```

The third problem I encountered is, that the Volume Control is adjusted wrong. When I adjust the volume with the volume keys on my notebook to 50 % I can't hear anything. Can I change these settings anywhere in the Gnome Config or in Alsa or wherever?

Is it possible to deactivate the touchstick and the touchpad via a hotkey? 

The last problem is, that when I turn the WLAN off via the Button on the my case, and turn it on again, it takes about 10 minutes until I see the WLAN Accesspoints in the List provided by the Networkmanager. Are there any commands like ipconfig /renew in Windows that refreshes the list of Accesspoints?

Thank for helping me (hopfully you could understand everything with my bad english)

schneida

---

### Post by Rob_Frohne on 2009-01-14
You can get your network back after turning off the wireless using the switch on the side of the computer by right clicking on the networking icon on the menu bar and disabling networking, and then right clicking again and re-enabling it again.

I am having difficulty with ALSA on my E6400.  With the alsa 0.17 from Intrepid, it makes crackling noises when a sound is played.  I installed alsa 0.18 and I get no sound at all now.

Your sleep problem may already be fixed by an update.  See this page if you are interested:

[https://bugs.launchpad.net/bugs/276943](https://bugs.launchpad.net/bugs/276943)

Rob

---

