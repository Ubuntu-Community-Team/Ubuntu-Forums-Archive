---
title: "unknown key pressed?"
date: 2008-11-07
forum: General Help
---

### Post by jon.reeve on 2008-11-07
keep getting this error appear in my syslogs, and it repeats a lot about every five minutes or so: 

Nov  6 10:36:08 pia kernel: [  831.173735] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Nov  6 10:36:08 pia kernel: [  831.173755] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Nov  6 10:36:33 pia kernel: [  856.220070] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Nov  6 10:36:33 pia kernel: [  856.220098] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.

but it'll give me these errors when I'm not doing anything, and I'm not touching the keyboard at all. I could run that command, setkeycodes, but I wouldn't know what keycode to give it, and I don't know what key this is supposed to be that is getting pressed. I guess I could try to map it to a 'blank' keycode, ie some kind of keycode that doesn't do anything, and maybe that will work. Does anyone know a keycode I could map this mystery key to? Or better yet, some information about this error and how I could resolve it otherwise?

---

### Post by dburnett77 on 2008-11-07
This error has been reported before.  Here's the link:

[http://ubuntuforums.org/showthread.php?t=76271](http://ubuntuforums.org/showthread.php?t=76271)

---

