---
title: "No clean shutdown"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by tsvim on 2006-03-06
Ok,

Ben running Ubuntu for about a month now (Yaay!!!) :) , for some reason when I shutdown my laptop (IBM T21, PIII 800Mhz, 20GB, 512 MB RAM), it stops after LVM something, meaning the screen won't turn off. Keyboard still responds (Hitting Enter moves to next line).

I think it might have to do something with the wifi card. (Once when it wasn't plugged in it actually did turn off completely) . I use a DWL-G650M with ndiswrapper.

Also, (although this should maybe be in the networking forum), whenever I turn the laptop on, it doesn't detect my wifi card immediately. The lights are on but for it to work, I need to configure the Network and activate the wifi card.

Actually, what I would like is to have an option during bootup to work with or without networking. (Most of the time I don't have access to network, this way I can save on battery time).

Thank you for your great support, you guys rock,

Tsvi M:confused:

---

### Post by aouie on 2006-06-07
I am not sure your problem is the same as the one you had, but you could try it anyways.
-------
If you are having freezes (or crashes) while shutting down (or logging out / log out / end current session) then disabling spash in the bootup / shutdown sequence should bypass the bug.
As pointed out in a different post
disabling splash from /boot/grub/menu.lst will bypass the shutdown freeze.
It worked for me (upgraded to Dapper, NVidia 5950, Athlon 64).
Sincerely,
Aouie

---

