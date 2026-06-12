---
title: "Install WUBI without CD drive"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by yalgret on 2009-10-12
I tried to install ubuntu on a friends computer (8.10)

It was a failure from the start because their CD drive was messed up and would not read the disk.

Is there a way to install [COLOR="Red"]WUBI [/COLOR] (inside windows) without an optical drive?

At the time I googled it and only found the full installation or a portable version

I have a working optical drive at home so I can use the CD to make a USB cd.

Thanks.

---

### Post by jagtesh on 2009-10-19
I needed to do exactly the same thing. Didn't have any blank CDs to burn it, so I tried mounting the ISO and installing it directly through WUBI from there.

I tried both the x64 and the x86 flavors of 9.10 beta. While I had a moderate success with the x86 WUBI install, I could only boot into the grub console after installation. And from that point, I was clueless so I tried re-installing and it got stuck this time. Tried again with x86. Got stuck again. I read the debug messages (CTRIL-ALT-F1) and it seemed like the installer was trying to access the CD (which I didn't have, obviously) and the installer was stuck at 0% or 5% during the different trails.

Hope someone can figure out a non-network workaround for this.

---

