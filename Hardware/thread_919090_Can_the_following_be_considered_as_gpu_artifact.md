---
title: "Can the following be considered as gpu artifact?"
date: 2008-09-13
forum: Hardware
---

### Post by extruct on 2008-09-13
Well I had a problem with my GPU. My GPU is Inno3D GeForce 6600 256MB AGP8x, but I wasn't able to enable nvidia driver to have hardware acceleration because my card recognized (both in windows and linux [I didn't have any problems in windows]) as nVidia GeForce Go 6600 GT PCIe16x. I found the only solution is to flash my GPU Bios with another bios with the same model but different manufacturer, and I did so. For now I'm running the card about 6-8 hours with the flashed bios. I have noticed some problem when desktop effects on. The problem shown on the attachment (look at the topbar its disappeared and have some random colors on in).
Is this may be considered as GPU artifact? Or desktop effects bug?

Thanks.

---

### Post by eggdeng on 2008-09-13
Looks like a window decorator problem. Have you got emerald installed and running?

---

### Post by extruct on 2008-09-13
No I don't have emerald installed.

---

### Post by eggdeng on 2008-09-13
You can install emerald and libemeraldengine0 from Synaptic. Then in Preferences-> Advanced Desktop Effects Settings, click on the window decoration icon and specify ```
emerald --replace
``` as the command.

---

### Post by extruct on 2008-09-14
I installed emerald and libemeraldengine0, but I don't have "Advanced Desktop Effects Settings" in preferences.
By the way I using Ubuntu 8.04 Hardy with kernel 2.6.24-19-generic and Gnome 2.22.3

---

### Post by eggdeng on 2008-09-14
I thought Hardy had the settings manager by default. In any case, you can install compizconfig-settings-manager from Synaptic and then proceed as above.

---

### Post by extruct on 2008-09-14
First of all thanks.
It didn't fix the problem, I also noticed that the problem occures only in oOO Writer and Eclipse sometimes.

---

