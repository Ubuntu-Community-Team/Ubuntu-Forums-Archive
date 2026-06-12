---
title: "dell latitude D810"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by tpariel on 2006-08-23
Hello,

I have a DELL latitude D810 and I installed the i8kutils (utilities for Dell Inspiron and Latitude laptops) but it doesn't appear to work. I gete this from the Adept Manager:


>conflict: i8kfan
>replaces: i8kfan

the rest thing seem to be ok. I cannot also use neither the volume buttons nor the Fn-keys.

Ariel.

---

### Post by hvbakel on 2006-08-24
You can get the volume keys working by creating a file named  
```
.xmodmap
``` in your home dir (it needs the '.' in front of the name). In this file put the following lines:

```

keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute

```

Then restart the X server (or reboot) and your volume keys should be working.

I'm not using the i8kfan utility, so I can't help you with that...

---

### Post by smelly_sox on 2006-08-24
DELL C640 runs i8kutils good. Suggest following; delete /usr/bin/i8kfan, use synaptic & mark i8kutils for 'Complete Removal', Apply, then re-Install. I also use gkrellm-i8k for the desktop and setting thermal specs.
Regards

---

