---
title: "How do i go to xgl from aiglx"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by Sbasi on 2008-02-13
Hi, I am running gusty on an x1400 using the new ati drivers. When I run compiz I have issues scrolling in firefox and was recommended to switch to xgl instead of aiglx. How do I switch down to xgl from aiglx? do i have to do a clean install or is there an easy way to do this?

---

### Post by jocko on 2008-02-13
This is what you need to do:```

sudo apt-get install xserver-xgl
```(Or find xserver-xgl in synaptic)

Restart the xserver (ctrl-alt-backspace). That's it.

---

