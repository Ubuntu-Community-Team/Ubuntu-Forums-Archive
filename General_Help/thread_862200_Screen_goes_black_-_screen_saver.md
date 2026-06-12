---
title: "Screen goes black - screen saver?"
date: 2008-07-17
forum: General Help
---

### Post by Vivaldi Gloria on 2008-07-17
In command-line-only Hardy install the screen goes black in ~10mins if I don't type anything. How can I change this setting?

---

### Post by alxlabs on 2008-07-17
I didn't do it myself, however I think that you should be able to find what you are looking for in /etc/console-tools/config - there are various DPMS options listed there

---

### Post by alxlabs on 2008-07-17
I think i found what you need. 
```

man setterm

```

---

### Post by Vivaldi Gloria on 2008-07-17
alxlabs,

I both changed /etc/console-tools/config and put a setterm line in rc.local. I don't know which one did it but it works. Thanks.

---

