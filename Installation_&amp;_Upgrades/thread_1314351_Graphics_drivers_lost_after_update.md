---
title: "Graphics drivers lost after update"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Jguy on 2009-11-04
Hi.

A couple weeks ago I downloaded and installed the updates through the update manager as part of 9.04. When I had done that, my graphics drivers were lost and I ended up having to reinstall them. I have an nvidia chip, so my graphics driver was/is named: NVIDIA-Linux-x86-185.18.36-pkg1.run. I have, according to lspci | grep -i VGA is an nVidia GeForce 8200M G (Rev a2)

Thinking this was a fluke or something I had messed up, I left it be. It is a slight inconvienience having to kill x and drop to a cli to install the drivers, but I could deal with it.

Today, I updated my laptop (still 9.04, I DID NOT update to 9.10) and the same thing happened, I got an error that said Ubuntu was now running in low graphics mode and my resolution changed to 1024x768 (VERY weird on a laptop screen, might I add).

Is there anything that would be causing my graphics settings/drivers to be lost on an update?

Thanks for any help you can provide.

---

### Post by norwoods on 2009-11-04
Is there anything that would be causing my graphics settings/drivers to be lost on an update?
yes.  there is a module that connects the video driver to the kernel that may not be updated if you did not install the video driver with apt/synaptic.  i installed the nvidia driver for 9.04 with System>>Administration>>Hardware Drivers which uses apt and have had good luck with updates.

---

### Post by Jguy on 2009-11-04
Ah, yeah. I just dropped out of X and installed it via their installer with sh ./NVIDIA*. I'll try reinstalling via apt or synaptic and see if I get better results. 

Thanks for the reply.

---

