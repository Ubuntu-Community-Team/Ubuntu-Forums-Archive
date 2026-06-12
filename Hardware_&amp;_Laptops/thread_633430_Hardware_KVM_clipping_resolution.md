---
title: "Hardware KVM clipping resolution"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by rollOver on 2007-12-06
**NOT KERNEL VIRTUALIZATION!**

Added a DVI KVM from [JustCom Technologies (JC-104UPA)]("http://www.justcomtech.com/product/off_jc102_104_upa_css.html") between my 2001FP Dell Monitor and my Gutsy box = black screen of death. Reconnect directly to the monitor, no problem. If I reduce resolution to 1280x1024 it works through the KVM (rated for 1600x1200@60Hz). My windows and mac boxes play nicely with this KVM, the **last** thing I expected to have touble with was my ubuntu box!!


I have been able to get the resolution to switch up to 1600x1200 but it pans and scans around a virtual desktop inside a 1280x1024 box. I am using an ATI Radeon 9800 card with the newst ATI drivers, BTW.

---

### Post by l33th41 on 2007-12-11
I have a JustCom KVM (JC-104A) and I'm experiencing issues as well. 

I have Windows boxes on ports 1-3 and Ubuntu Gusty on port 4. If i select port 4 on KVM and then turn on Gusty box I experience the panning and scanning you refered to... 

However, if I select any of the other ports, turn on my gusty box and wait for it to completely load, then switch to port 4 on KVM, display is normal.

Gusty box is a Sony Vaio laptop with Ati IGP.

---

### Post by rollOver on 2007-12-12
Thanks for sharing, how do you set the resolution to begin with? I connect the monitor straight to the box to set it to 1600, reboot and then do as you indicated, the box is black at the sign in screen--then if I do a blind sign in it comes up with a 1280x1024 desktop. So frustrating!

Update: I ordered an Nvidia GeForce 5800GS so that I would have a more ubuntu friendly driver set and to take advantage of PCI-E on my system. It works right out of the box with this switch, I am a very happy ubuntu'r!

---

