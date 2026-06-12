---
title: "Dual Processors (CPU's)"
date: 2005-11-19
forum: General Help
---

### Post by tgunner on 2005-11-19
I am fairly new to linux, and will soon be installing ubuntu 5.10 on a dual pentium 733 machine. From reading other posts about this, I have seen that people generally have problems with the OS recognizing the second processor. I need to know how to correctly do this, please don't just give guidelines, I really need step-by-step instructions. Thanks in advance! :cool: :cool:

---

### Post by suRoot on 2005-11-19
Honestly, a lot of it is application specific - some apps know to use SMP while others don't.  You don't say how you're using this box - server use or workstation use, but it's been my experience that getting Linux to work on SMP boxes isn't that difficult.

I've not installed Ubuntu on an SMP box, so I don't know whether it correctly detects the second processor & installs the correct kernel.  My guess is that it doesn't, but I could be wrong.

If you install & find that you're using the linux-386 kernel, open up synaptic & install the linux-686-smp kernel.  Do this by going to System -> Administration -> Synaptic from the menu.  Once you open synaptic, search for (click the search button on the toolbar) linux-686-smp.  Click it to install & then click apply on the toolbar.  Reboot & the box should boot the smp kernel.  You can verify by running uname -r from a console (kernel name should indicate smp).

From there, you may need to tweak specific apps to use the second processor.  You may want to give more info as to how you plan to use this box & what apps you'll be running.

---

