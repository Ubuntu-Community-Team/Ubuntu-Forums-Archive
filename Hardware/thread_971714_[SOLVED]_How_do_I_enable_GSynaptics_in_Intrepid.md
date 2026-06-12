---
title: "[SOLVED] How do I enable GSynaptics in Intrepid?"
date: 2008-11-05
forum: Hardware
---

### Post by mgangav on 2008-11-05
Well, when I try to change my touchpad preferences, I get the following message: 

> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics


Ok, so after following the advice of some of the threads here, it seems that I have to edit xorg.conf in some places. But, the xorg.conf file in Intrepid 8.10 is different than from previous versions. What should I do?

---

### Post by mgangav on 2008-11-05
Ok, nevermind I just followed the instructions on [**this page**]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig")

---

### Post by Magnes on 2008-11-05
I have similar problem with my tablet. It doesn't work and uncommenting lines in xorf.conf that were commented during the upgrade to Ubuntu 8.10 causes the X server not to start. Have you reported a bug?

---

### Post by pelle.k on 2008-11-05
If you run intrepid, and just want to enable/disable synaptics from time to time, just do it in mouse preferences. No need to enable shmconfig to do only that.

---

