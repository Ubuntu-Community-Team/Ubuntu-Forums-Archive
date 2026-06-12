---
title: "How to fix screen flickering"
date: 2020-09-28
forum: Hardware
---

### Post by satimis on 2020-09-28
Hi all,

Just purchased a new Dell 4K 31.5" U3219Q display.  It flickers now and then occasionally, turning to a black screen and back in about 5 to 15 seconds.  It happens sometimes automatically and another time when I click the mouse.

The HDMI cable is having metal shell soven mesh cover and ferrite bead at both ends.

Please advise how to fix the problem?

Thanks

Regards

---

### Post by Bashing-om on 2020-09-28
satimis; Hello -

Please provide us with what graphics are provisioned on this Dell system:
```

lspci -k | grep -iEA5 'vga|3d'

```

What release you are running:
```

lsb_release -a
uname -a

```

Maybe some known works.

[INDENT]could be
[/INDENT]

---

