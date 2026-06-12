---
title: "Working touchpad, but computer says it doesn't exist?"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by MdaG on 2005-09-07
I'm trying to disable my ALPS touchpad using tpconfig, but the computer claims it doesn't exist.

```
$ sudo tpconfig --tapmode=0
fatal: 

No Synaptics or ALPS touchpad device found
```

Heeeeeeeeeeeeeeeeeelp. It's working fine, I don't want the tapping feature...

---

### Post by s_p_a_r_k_y on 2005-09-07
are you using the synaptics drivers for your mouse in xorg.conf?

---

