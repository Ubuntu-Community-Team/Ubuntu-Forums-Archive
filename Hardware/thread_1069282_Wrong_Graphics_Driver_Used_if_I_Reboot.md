---
title: "Wrong Graphics Driver Used if I Reboot"
date: 2009-02-13
forum: Hardware
---

### Post by AgentE382 on 2009-02-13
I use Ubuntu Hardy Heron 8.04LTS x64, installed from the minimal CD. After installation, I ran
```
sudo apt-get install xubuntu-desktop
```
I downloaded "NVIDIA-Linux-x86_64-180.29-pkg2.run", switched to runlevel 1, and ran
```
sh NVIDIA-Linux-x86_64-180.29-pkg2.run
```
and installed the driver.
I then switched to runlevel 5 without rebooting, and everything was fine. I tested the driver by playing gl-117. After I rebooted, Ubuntu said it was running in low graphics mode. I repeated the process above, and it worked. Now I'm stuck. If I want to use 3D applications, I have to reinstall my driver every time I reboot. Anyone have any ideas?

---

### Post by tenmoi on 2009-02-14
as far as i can remember you'll have to remove all the *-linux-restricted-module* and *nvidia* (it's been quite a while back when i was running an nvidia card so you'll have to search this forum for how to install your nv card)
Then you do a ctrl+alt+f1 and /etc/init.d/gdm stop and start installing the driver.
That's the proper way to go.

Keep my fingers crossed for you!

---

### Post by AgentE382 on 2009-02-16
Thanks, tenmoi.

I have a question, though. When I try to uninstall *linux-restricted-modules* or nvidia-kernel-common, Synaptic wants to uninstall linux-generic. Is that okay?

AgentE382

---

### Post by AgentE382 on 2009-02-16
*Thanks, tenmoi!!!,*

I ran ```
sh NVIDIA-Linux-x86_64-180.29-pkg2.run --advanced-options
```waded through everything, and found exactly what you said. The installer searches for those files, but only uses the RedHat Package Manager. I uninstalled them, and now, everything works great!

AgentE382:D

---

