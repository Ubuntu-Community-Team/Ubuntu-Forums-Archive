---
title: "nvidia-settings bug? Help!"
date: 2008-08-12
forum: General Help
---

### Post by strange_cathect on 2008-08-12
When I attempt to use nvidia-settings to set up my preferences for dual screen and resolution, I continue to get the same error message:

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

However, I can confirm that the driver is **enabled** and **in use** in the Hardware Drivers. And following the directions in this error message does not resolve the issue.

Sound familiar?

---

### Post by NT4usB on 2008-08-12
Are you running nvidia-settings as root?
(No idea if it would cause this error or not, just tossing it out.)

---

### Post by tuxxy on 2008-08-12
what driver are you using? is the open source driver?

search synaptic and see if the nvidia-glx or nvidia-glx-new drivers are installed

If theres a conflict and both are installed, remove aka nvidia-glx and try your driver again.

---

