---
title: "Compaq nx9010 only some hotkeys works"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by lorenzo on 2005-05-20
Ciao,
I'm trying to configure hotkeys on my compaq nx9010 but only some of them works. E.g. "volume up", "volume down", "mail" "i" works correctly but "mute volume" "lock button" "? button" doesn't work.

I've tried to switch different keyboard layout but no luck so far. Any suggestion?

Thanks,
Lorenzo

---

### Post by gasparov on 2005-05-20
[QUOTE=lorenzo]Ciao,
I'm trying to configure hotkeys on my compaq nx9010 but only some of them works. E.g. "volume up", "volume down", "mail" "i" works correctly but "mute volume" "lock button" "? button" doesn't work.

I've tried to switch different keyboard layout but no luck so far. Any suggestion?

Thanks,
Lorenzo[/QUOTE]
 Hi,
   I haven't done it yet but on my nx9030 just volume keys works out of the box,that is no mail/find/etc keys and even no screen brightness,but they do are "recognized by the kernel".
After pressing a key
```

tail /var/log/syslog

```
it should tell you something like this
```
May 20 15:41:32 localhost kernel: atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
May 20 15:41:32 localhost kernel: atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
May 20 15:41:32 localhost kernel: atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
May 20 15:41:32 localhost kernel: atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.

```

Note that the entries are 2,one for pressing the other for releasing
So there is a way but right now I'm getting too fun with acpi & C.

By the way,can I ask you about battery and wifi? Battery is 3 hours (but not checked carefully)in idle here.Wifi is cool after editing /etc/network/interfaces to save boot time during boot.
Hi  (da Trento)

---

### Post by lorenzo on 2005-05-26
I'm still trying to make those keys work. So far, no luck. Some hotkeys just seems not to be recognized. I've tried some tests (can't remember the command). It appear a box on the screen and when you move the mouse or you touch the keys, values are written on the console. But for some hotkeys, no values came out. Plain dead.

About network. I just set al interfaces to "no auto" and commented "#" the lines about hotplug. Now boot is much faster. All the job is done by ifplugd when I plug something (ethernet cable or wireless).

My battery is old (2 years) and last 1 1/2 hour. Sigh! 

What I really miss is suspend/hibernate. I can suspend/hibernate. But I can't resume  :-? 

ciao,
lorenzo

---

### Post by nmincone on 2006-12-17
nx9010 running 6.10 (Edgy) the following hot keys work without modification;
screen brightness (up/dwn)
volume mute, up/down
mail (defaults to Evolution)
internet (defaults to Firefox)
but nothing else. Anyone have any success resolving this one too?

---

### Post by frankabel on 2007-05-11
What Keyboard layout is the correct for Compaq NX9010? I just install Xubuntu and not configure it correctly at the installation steps, so I want right now run some kind of program that reconfigure my keyboard guessing my keyboard layout asking me to press some keys etc. like the installation program. What program can I run to reconfigure my keyboard?

---

