---
title: "Nvidia won't let my fan turn off"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by KARaidl on 2008-01-02
I just installed the proprietary Nvidia driver 169.07 for an 8800GT because I wanted to see all the nice Compiz Fusion goodness. Ubuntu would never let me do this through the Restricted Drivers Manager, and I read in some list that they had yet to include the proprietary driver for the 8800GT. So instead I installed it through Envy. Everything went smoothly and I've got my desktop effects enabled.

The only issue is now my video card fan is constantly on, and it's loud and annoying.

Can anyone think of a reason why the proprietary driver would be doing this?

---

### Post by Shakey_Jake33 on 2008-01-05
I hit the same problem.  By default the drivers seem to run at maximum fan speed.  To get around this, I installed nvclock (availiable in Synaptic Package Manager),  Once installed, I opened a terminal and typed 'nvclock -f -F auto'.  This changed the fan speed to it's normal 'auto' and all was good!

---

