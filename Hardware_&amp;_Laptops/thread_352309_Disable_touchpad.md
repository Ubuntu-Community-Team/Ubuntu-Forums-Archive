---
title: "Disable touchpad?"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by eilu on 2007-02-03
Is there a way to disable the synaptics touchpad? There's a hardware button on my notebook that's *supposed* to do so, but doesn't (it's the only hardware button that doesn't work)

I managed to google this: [http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/) and tried to do as it said, I added
```
Option “SHMConfig” “on”
```

to the touchpad sectionj of xorg,conf but it keeps throwing errors (gdm won't load) and I have to revert to the backed-up copy. Any idea on what I could be doing wrong?

---

### Post by niekko on 2007-02-03
Have you tried disabling it in BIOS settings?

[[COLOR="Blue"]https://help.ubuntu.com/community/SynapticsTouchpad[/COLOR]]("https://help.ubuntu.com/community/SynapticsTouchpad") might have helpful information for you.

---

### Post by eilu on 2007-02-04
Yes, thank you. Finally got it working the way I need it to. Thankfully didn't need to disable it in BIOS.

---

