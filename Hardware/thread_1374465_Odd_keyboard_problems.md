---
title: "Odd keyboard problems"
date: 2010-01-06
forum: Hardware
---

### Post by Blice on 2010-01-06
Hi,

I'm helping someone with their Acer Apsire One...  Apparently they've had this problem with multiple version of Ubuntu and some other distros; wondering if anyone has any ideas.

When typing, the keyboard will start entering a random "wtru" places while you type, and then eventually the keyboard just stops working. I went ahead and booted straight into bash without X to see if it was just an X problem but it isn't- the keyboard starts entering these random characters from time to time.

However, in the console it actually gave me an error message (dmesg) whenever it happened, which is:

atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.

Thank you!

---

### Post by augusto on 2010-03-02
Blice, I've got the exact same problem with my Acer Aspire One except mine types "sehyi" at random times or will repeat a key over and over again, rendering it useless at times. It does not seem to matter what program I'm running since it happens in Firefox, OpenOffice and in the shell. Did you ever resolve the issue? I'm thinking of doing a fresh install though I think it's more likely a hardware issue. Thanks

---

