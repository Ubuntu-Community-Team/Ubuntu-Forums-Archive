---
title: "Per-user Touchpad Settings"
date: 2008-11-12
forum: Hardware
---

### Post by Xyem on 2008-11-12
I'm doing a minimal installation of 8.10 on my laptop and I was wondering how to get per-user touchpad settings ( such as click-tap etc. ). I believe GNOME does this ( System -> Preferences -> Mouse ) but I don't know if this is system-wide or not?

As a side-question, shouldn't 'xorg' now depend on 'hal' as it now uses it to find input devices? :confused: I have to install it separately otherwise my touchpad doesn't work..

---

### Post by wgrant on 2008-11-12
GNOME touchpad settings are per-user.

xorg works fine without hal; it just requires some extra configuration. Desktop users have hal installed by default.

---

### Post by Xyem on 2008-11-12
Thanks for the information, it is helpful to know that.

Can I get the per-user touchpad settings without running GNOME? I would like to use other WMs ( like Fluxbox ).

---

### Post by wgrant on 2008-11-12
You can use 'xinput' to set most touchpad options at runtime.

---

### Post by Xyem on 2008-11-12
So if I have two X sessions up, they will have independent settings?

---

