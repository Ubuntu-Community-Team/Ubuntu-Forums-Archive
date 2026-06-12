---
title: "Does not find all RAM"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by ManLord on 2005-08-29
I have 1280 MB of RAM, one 1024 MB, and one 256 MB. But in when i check ksysguard, or run "free" in console, it show only 906656 KB. How can this be?? It's not even one full 1024 module...

Please help, KDE needs all the RAM it can get :)

Also: Is it normal that KDE uses like 874000 KB memory? I'm just surfing and playing some music..

---

### Post by varunus on 2005-08-29
Very simple fix.

Just install linux-686 from synaptic.  This will let you use all of your RAM.

Ubuntu comes with a 386 kernel by default, which tops out a 900 MB.

---

### Post by luca_linux on 2005-08-29
You're probably running a 386 kernel, aren't you?
You need to install and run a 686 kernel.

---

### Post by luca_linux on 2005-08-29
Varunus, it seems like we've posted in the same time. :grin:

---

### Post by ManLord on 2005-08-29
Do I have to restart or something? Doesn't find the extra RAM now.

And in case you missed my edit:
Also: Is it normal that KDE uses like 874000 KB memory? I'm just surfing and playing some music..

---

### Post by varunus on 2005-08-29
Yes, you need to restart and choose the 686 hoary kernel from the list.  (If you've done any kernel modifications or proprietary drivers, you may need to redo them).

Part of that RAM usage is misleading; this is the VM size, not the resident memory size.  I believe you can set the system monitor in KDE to show you the resident memory size (you can in GNOME, at least).  Linux expands to fill your RAM, and uses everything not used by programs as a large disk cache (so the computer speeds up the longer its on).  So don't worry about the usage.

---

### Post by ManLord on 2005-08-29
Ok, thanks for the help!

---

