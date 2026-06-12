---
title: "something is taking all my RAM"
date: 2008-10-14
forum: General Help
---

### Post by enzo12345 on 2008-10-14
Hi.

im using ubuntu hardy heron desktop.

latly it has been running very slow, when you move the mouse it jolts about, and programs are not running fast anymore.

specs:athlon xp 2500, 512mb ram, 128mb ati radeon.

When I open system monitor it shows me my ram is 95% taken and my swap file is 100% used.

I have looked at the processes tab and the most any one program is taking is 20mb.

How can I find out what is taking all this memory, and are their any ram optimization programs for linux?

Thanks

---

### Post by SuperSonic4 on 2008-10-14
Can you post: ```
top
```
This tells you a list of what's using the most ram.

---

### Post by enzo12345 on 2008-10-14
thanks, tried it out.

I restarted my computer and its working fine at the moment.

I think it starts to go slow when i search using nautilus, or open nautilus as root by doing

```
sudo nautilus
```.


A process called Xorg is top.

---

