---
title: "Problem with dual displays on nVidia GeForce GTX 260"
date: 2012-02-01
forum: Hardware
---

### Post by P-J on 2012-02-01
Hi all,

I've managed to get Twinview working on my monitors using the 'nvidia-settings' program, but it's screwed up my file browsing windows and dialog boxes.

When I go to my home folder, I get a display like the screenshot with huge fonts, nasty looking controls and no icon images.

Anyone got any thoughts? I'm using the closed source driver.

Cheers, Phil.

---

### Post by wolfen69 on 2012-02-01
Check your *Universal Access* settings.

---

### Post by P-J on 2012-02-01
> **wolfen69 said:**
> Check your *Universal Access* settings.

Just checked there now. All normal. Any other ideas?

---

### Post by P-J on 2012-02-01
Nevermind, fixed it now with help from a chap on IRC.

Just need to add...

```

Option     "DPI"  "96 x 96"

```

...to the monitors section in the xorg.conf.

Cheers.

---

