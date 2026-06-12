---
title: "Ubuntu 8.04.2 install not updating MBR"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Xuor on 2009-05-22
I used to have a Wubi install of Ubuntu 8.04.x running happily on this machine. Then I upgraded to Windows 7 and blew away my MBR. I am attempting to restore it by re-installing 8.04 via Wubi, then replacing my root.disk file with my original.

The problem arises in the install process--my mounted ISO of 8.04.2 steadfastly refuses to change the MBR. I am never prompted on boot to pick an OS, and msconfig/boot shows only Windows.

The exact same procedures with 9.04 result in a perfectly edited MBR. But I need 8.04, not 9.04. And the weirdest part is this: Earlier on in this re-install process, when I was trying different things, the 8.04.2 mounted ISO Wubi install edited the MBR quite happily. Now, under presumably identical circumstances, it refuses to touch it.

---

