---
title: "Kernel panic... VFS Unable to mount... unkonwn-block(0,0)"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by AlanRick on 2009-05-21
Jaunty was giving me problems so I formated the unix partition and did a fresh 8.10 install since that's what I'd used earlier.

Install worked but when I boot and select ubuntu in grup I get the message
```
[0.776111]kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0).
```

The old windows xp boot still boots from grub okay.

Somewhere I read that the error is caused when the grub menu reads the wrong root. So I edited menu.lst and added the line

```
root  hda(0,6)
```   
below the ubuntu entry (first menu item).
This is because gparted is showing the ubuntu partition as hda7. 

It still does not work. And the same happens when I do an 8.04 install.  
Any ideas?

---

### Post by AlanRick on 2009-05-21
Solved.
My previous post was a red-herring. 
I installed 8.04  half a dozen times sometimes formating the partition in advance, sometimes just deleting the partition with no success.

Maybe it was the fact that I left the room while it did the last install but maybe it was because in the last install I switched the pc off when the message appeared said "remove cd..." while rebooting after install finished.

Anyway, it now works.

---

