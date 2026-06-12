---
title: "nv driver for 8.10 upgrade"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by frisket on 2009-10-25
I'm trying to crank an old Dell Dimension 4550 up from 8.04 to 8.10.

It has an nVidia GeForce4 card, which was supported under 8.04, but not under 8.10, and I found numerous web pages saying that the 8.10 installer would therefore set the new installation to use the open-source nv driver (and forego 3D graphics etc, which is fine by me).

Clearly this isn't the case. The installer duly issued a warning that the nVidia card wasn't supported, but instead of setting it up for nv, it went ahead and set it up for the unsupported driver. I now have a system which boots as far as the username/password graphics screen, but then hangs with the throbber frozen and the keyboard lights lit, requiring a hardware reset.

Booting in single-user mode shows that /etc/modprobe.d contains a file called nvidia-kernel-nkc. /etc/xorg.conf is a dummy file with generic entries only, but my 8.04 xorg.conf is preserved under a dated name. What is "nkc"?

I can find a gazillion web pages about how to coax Ubuntu into using the newer nvidia drivers, but I want the opposite; to use the nv driver, just to get the system usable. I can worry about upgrading later.

Can anyone please point me at docs on how to undo this faulty setup and force the system to use the nv driver?

///Peter

---

### Post by frisket on 2009-12-11
> **frisket said:**
> I'm trying to crank an old Dell Dimension 4550 up from 8.04 to 8.10

Anyone else trying this, forget it. Wipe and install 9.10 or later and it works.

P

---

