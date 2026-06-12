---
title: "Sony Vaio brightness FN keys"
date: 2010-12-29
forum: Hardware
---

### Post by Red_Beret on 2010-12-29
Hey,

I have a Sony VAIO VGN-FE21B, and Ubuntu 10.10 installed on him.

However, i can't adjust the screen brightness through the function keys.

When i press the keys, Ubuntu shows me the notification, so, the keys are being decoded correctly, as i can see if i execute this instructions:

```
procyon@procyon:~/Área de Trabalho$ xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
keycode 232 = (keysym 0x1008ff03, XF86MonBrightnessDown), state = 0x0
keycode 232 = (keysym 0x1008ff03, XF86MonBrightnessDown), state = 0x0
keycode 233 = (keysym 0x1008ff02, XF86MonBrightnessUp), state = 0x0
keycode 233 = (keysym 0x1008ff02, XF86MonBrightnessUp), state = 0x0

```

However, the screen brightnes keeps the same

If i adjust through Nvidia drivers interface, works fine, so is not a hardware issue.

Can anyone help me?

thx

---

### Post by Red_Beret on 2010-12-29
I've installed the package smartdimmer, and works fine, except with the flag -i, that increases brightness... any ideas?

---

### Post by Red_Beret on 2010-12-29
Nevermind, i've already solved my problem based on this -- [http://ubuntuforums.org/showthread.php?t=1304658&highlight=smartdimmer+increase](http://ubuntuforums.org/showthread.php?t=1304658&highlight=smartdimmer+increase)

---

