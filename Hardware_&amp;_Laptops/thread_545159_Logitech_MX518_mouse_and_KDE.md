---
title: "Logitech MX518 mouse and KDE"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by bluetracer on 2007-09-07
Hi,

(Vital stats - Feisty, fully patched, AMD64)

Sorry to make a new thread for this but I can't find the exact problem anywhere.

I mostly use Gnome, but occasionally use KDE.  Accordingly, I run KDE with GDM.

I have a Logitech MX518 mouse, which I have configured in xorg.conf according to the guide on the Wiki and which works fine in Gnome.

In KDE, however, the back/forward buttons scroll up and down, and the scroll wheel does nothing.

I've googled this a fair bit, and apparently KDE can ignore xorg.conf when using GDM.  However, the only fix I could find was specific to Gentoo.

Can anyone help?

---

### Post by biophysics on 2007-09-07
I think there is a config file in ~/.kde/share/config/"****"  (I am not in kubuntu for the moment sorry). Just delete it from gnome and relogin to kde (Do not do it from KDE).

---

### Post by bluetracer on 2007-09-07
There are, at a conservative estimate, 7.5m files in that folder! :-D

None of them have "mouse" in the name.  Do you know which one I should rm?

THanks!

---

