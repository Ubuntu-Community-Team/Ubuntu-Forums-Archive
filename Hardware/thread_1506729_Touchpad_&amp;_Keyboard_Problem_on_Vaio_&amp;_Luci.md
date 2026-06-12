---
title: "Touchpad &amp; Keyboard Problem on Vaio &amp; Lucid"
date: 2010-06-10
forum: Hardware
---

### Post by jack24 on 2010-06-10
When I use the laptop keyboard, it misses every few keystrokes and when I use the touchpad, the cursor hesitates in mid move.  Just started (possibly after last kernel upgrade).  

Sony VAIO VPCS111FM
Ubuntu Lucid 64bit 2.6.32-22 generic

Touchpad & keyboard enabled in gconf.
No assistive technologies enabled.

I get this in kernel log:
> Jun 10 12:08:34 l kernel: [ 1144.919083] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Jun 10 12:08:34 l kernel: [ 1144.925437] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Jun 10 12:08:34 l kernel: [ 1144.926694] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jun 10 12:08:34 l kernel: [ 1144.937392] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
Jun 10 12:08:38 l kernel: [ 1148.132228] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Jun 10 12:08:38 l kernel: [ 1148.137409] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1

dmesg shows:
> [   14.725868] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   14.746354] Console: switching to colour frame buffer device 170x48
[   14.771782] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9

Doesn't seem to be same as Bugs #549727, 554050, or any of the others I found that mention touchpad or keyboard problems. 

I could really use some help if you have any ideas.

---

### Post by moboticdes on 2010-10-27
Same problem, keyboard misses some key strokes(randomly,not any particular keys), fr instance this is wrtten withot doule typingmissinkeys, as you cn see the keboard misesquite frequently the spceand th "a" charachers.
Also the cursor of the touchpad hesitates a little in mid-screeen and the orange charging led flashes 4 times every second even if battery is charged.

It happened suddenly with computer on and no specific update, therefore think it is hardware related, I'm using a 4 months old (however kept and treated as new) Sony Vaio VPCS11E7E

I loved this vaio laptop however this unprovoked hardware glitch quite put me down!
thankyou

---

### Post by moboticdes on 2010-10-27
> **moboticdes said:**
> Same problem, keyboard misses some key strokes(randomly,not any particular keys), fr instance this is wrtten withot doule typingmissinkeys, as you cn see the keboard misesquite frequently the spceand th "a" charachers.
Also the cursor of the touchpad hesitates a little in mid-screeen and the orange charging led flashes 4 times every second even if battery is charged.

It happened suddenly with computer on and no specific update, therefore think it is hardware related, I'm using a 4 months old (however kept and treated as new) Sony Vaio VPCS11E7E

I loved this vaio laptop however this unprovoked hardware glitch quite put me down!
thankyou

Ok solved, let's sum up the situation:
1. yes the problem was hardware related
2. the logs of Linux however didn't show any hardware problem or glitch, no "lost sync" message in the logs for the Touch Pad for instance.

So the problem was hardware related however not shown on any logs, however the flashing charging led should have given me a hint...

REMOVE FAULTY BATTERY AND TRY WITHOUT WITH AC POWER ONLY,

I did it without even rebooting the computer and my Sony VAIO VPCS11E7E now is back from the black :guitar::guitar:

Strange thing for a faulty battery to give glitches to both mouse and keyboard however this topic is now SOLVED.

thank you all

---

