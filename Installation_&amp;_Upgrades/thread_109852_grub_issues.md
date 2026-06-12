---
title: "grub issues"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by nathan43081 on 2005-12-29
every time I install a new kernel grub resets it's menu.lst file and my hd settings are off. I need to know where these settings are so that I can make the correction and not have this pain every time I upgrade the kernel. Does anyone know where these settings are or know a way to reset them.

Thanks,
Nathan43081

---

### Post by gruepig on 2005-12-29
/boot/grub/device.map perhaps?

---

### Post by Sutekh on 2005-12-30
How do you install your new kernels, do you use Synaptic?  What do you mean by your hd settings are off?  What problems do you have?

---

### Post by nathan43081 on 2005-12-30
I use synaptic to do my updates and it gets my new kernels. When I go to reboot after doing the updates, I have to edit my grub.conf file to reset the root(hd*,*) information to the correct drive. I don't know where this default setting is, but it changes back to incorrect settings every time that I change my kernel. The settings in device.map are correct.

---

### Post by Sutekh on 2005-12-31
Ok, could you post your device.map and menu.lst here?

---

