---
title: "No battery found: strange issue"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by madchicken on 2005-06-27
Hi all.
I'm running Ubuntu 5.04 on a Sony Vaio PCG-K195HP and my battery isn't recognized from the system (I also cannot hibernate my laptop, but this is another story :-) ).
I've found a workaround to make the battery work for me...I post this solution here so someone can help me to find a "real" solution to this problem.

The trick is simple: my problem is that the battery module can't start properly during a normal boot, so I have to shut down it and reload it in the kernel to make it work:

```
sudo modprobe -r battery
sudo modprobe battery
killall gnome-panel

```

The last command is only to refresh the battery applet in the panel.
I can't understand why this happens (there's no errors in the startup log...it simply say "No battery found"), but the workaround works for me, maybe it works for you too.
I hope there is someone here that can help me making the boot process work without unloading/loading the battery module.

Thanks.

-- Pierpaolo

---

### Post by zakili on 2005-06-28
i had same problem, then i recompile kernel with battery include

---

