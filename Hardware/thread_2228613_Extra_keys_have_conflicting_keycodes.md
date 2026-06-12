---
title: "Extra keys have conflicting keycodes"
date: 2014-06-08
forum: Hardware
---

### Post by NickLanam on 2014-06-08
Hello,

I recently got my hands on a Steelseries MERC Stealth - basically, a keyboard with an extra pad of gaming keys on the left. I bought this to replace my existing Ideazon MERC (not the Stealth variant).

I attempted to use xmodmap to bind all of the extra keys to my liking, as I'd done before with the older version. However, I discovered that all of the keys in the "gaming terrain" area had the same keycodes as the keys with which they shared a label. That is, the "Caps" key on the terrain has the same keycode as the real Caps Lock key, and so forth.

No problem, I've had this happen before with the old keyboard (on several versions and flavors of Linux) - and I usually use [FONT=Courier New]setkeys[/FONT] to change the keycodes for those keys. So, I used '[FONT=Courier New]showkey -s[/FONT]' to get the scancodes, thinking I could change the mappings. No dice: the scancodes match too. I did a little digging, and found the '[FONT=Courier New]atkbd.softraw=0[/FONT]' kernel parameter. I applied this, and even that did not give me any way to distinguish the duplicates.

Are there any other files or kernel parameters I can get in to for this?

So far, my research has turned up [xmodmap basics](http://unix.stackexchange.com/questions/49650/how-to-get-keycodes-for-xmodmap), [a listing of kernel parameters](https://wiki.archlinux.org/index.php/kernel_parameters), and a topic about [a very similar situation](https://bbs.archlinux.org/viewtopic.php?id=43662), among some less useful links.

**TL;DR:** Bought a keyboard with some extra keys, extra keys have the same scancodes as regular keys, rendering them impossible to remap. I want to remedy this.

Thank you!

---

