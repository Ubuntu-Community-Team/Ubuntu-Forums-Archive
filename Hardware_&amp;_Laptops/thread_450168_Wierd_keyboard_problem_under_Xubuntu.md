---
title: "Wierd keyboard problem under Xubuntu"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by febrile on 2007-05-21
Hardware: Aopen Notebook 1557G (an oldish laptop)
OS: Xubuntu feisty and WinXPpro dualbooting

I'm getting odd keylocks randomly every couple minutes. I'm typing normally and a key just repeats till the next keystroke. My first instinct is to blame my hardware, but the keyboard works just fine under WinXP. I don't remember if it started when I upgraded (clean install) to feisty a couple of weeks back, or since then. I can't see any particular pattern in which keys lock up & it's done it twice while writing this - annoying.

- Anyone else seen something similar?
- Are there any configs/logs I should look at to help diagnose?

Random thought: could it be an overheating issue? (like most, my laptop seems to run hotter under Linux than Windows)

Thanks

---

### Post by febrile on 2007-05-24
bump

Any thoughts anyone?

---

### Post by siglost on 2007-05-25
are you using the mouse or thumbpad while it happens?  I have learned that events, such as my 10 button Logitech Lazer mouse dont always map correctly, and that there may be multiple events mapped to one function.  (i.e. when I press the scroll button, it creates a new tab instead of the regular scroll lock)

I havent delved too much into how X maps these things, but that might be a good start for you.

Good luck!

-d

---

### Post by febrile on 2007-05-25
Hey siglost, thanks for the reply.

I'm not using mouse when I get the keylock issues. I don't tend to use the mousepad that much and I'm too primitive to be up to using keyboard and mousepad at the same time.

But now you mention it I see I do get temporary mouse pointer freezes sometimes as I track the mouse across the screen. So your suggestion of confusion in X's mapping of keyboard and mouse events sounds like it might be a useful lead :). I'll have a look into it - I know nothing about how all this works, but I'd guess a bit of searching will give me some clues. Any hints/links from folks out there would be greatly appreciated.

[EDIT] Afterthought: I don't remember ever having any keyboard/mouse problems in edgy. Did X's keyboard/mouse event mapping change a lot from edgy to feisty?

---

### Post by AmpDivorax on 2007-05-25
I am having the exact same problem and it's annoying me quite a bit.  Any and all help on this one is appreciated.  I will also mention that I am using a USB keyboard and USB mouse, but the same effect happens on my PS/2 keyboard as well.

---

### Post by febrile on 2007-05-26
ok, a bit more detail here.
I see my /var/log/kern.log lots of psmouse.c and atkbd.c lines like

```
May 26 08:39:44 febrile kernel: [  213.316000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
May 26 08:39:44 febrile kernel: [  213.320000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
May 26 08:39:44 febrile kernel: [  213.320000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
May 26 08:39:44 febrile kernel: [  213.324000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
May 26 08:39:44 febrile kernel: [  213.324000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
May 26 08:39:44 febrile kernel: [  213.324000] psmouse.c: issuing reconnect request
...
May 26 08:48:21 febrile kernel: [  727.692000] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
May 26 08:48:21 febrile kernel: [  727.692000] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.
...
May 26 09:09:39 febrile kernel: [ 1999.872000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
May 26 09:09:39 febrile kernel: [ 1999.876000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
May 26 09:09:39 febrile kernel: [ 1999.884000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
...
May 26 09:38:08 febrile kernel: [ 3703.120000] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
May 26 09:38:08 febrile kernel: [ 3703.120000] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.
...
May 26 10:10:38 febrile kernel: [ 5644.636000] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
May 26 10:10:38 febrile kernel: [ 5644.636000] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.
```

These coincide with the temporary mouse and keyboard freezes I've been getting.

@AmpDivorax: do you get similar messages in your kernel log?  
@siglost: is this the sort of thing you were suggesting?

If it helps, my system is
```
$ uname -a
Linux febrile 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```
In the kernel log the boot sequence shows these lines for my keyboard (I think) and my mousepad:
```
May 26 10:59:37 febrile kernel: [   16.691782] serio: i8042 KBD port at 0x60,0x64 irq 1
...
May 26 10:59:37 febrile kernel: [   26.124000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
May 26 10:59:37 febrile kernel: [   26.168000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
```

---

### Post by AmpDivorax on 2007-05-26
I am not seeing those lines in my kernel log so this is now making me rather curious on what is causing this issue.  I can also confirm that I don't experience this issue when I am in bash mode so it may be a problem with Xorg.

---

### Post by slambrick on 2007-05-26
I also find some weird things under Ubuntu and my wireless logitech mx5000 keyboard. often when I startup I cannot access anything until I hold down the Left CTRL key while clicking something. after I have done it everything seems OK. I have no idea why so any clues would be useful.

---

