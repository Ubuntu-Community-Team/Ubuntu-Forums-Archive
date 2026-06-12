---
title: "NVIDIA Excepts Restricted Problem"
date: 2009-07-02
forum: Hardware
---

### Post by ronaldprettyman on 2009-07-02
Ok I built a machine for my cousin, It has an nvidia 6200 agp in it. The easiest bet would be just to buy a new one but money is tight so thats not an option.

Situation. Restricted drivers don't work when installing them from apt, they work fine on all my other systems, but this system doesn't like them.

I am using the nvidia installer from Nvidia and that one works. The one's from the restricted don't.

Now everytime a kernel update comes through it breaks the system until he reruns the installation.

My idea right now is to just write a script that logs the current version on boot and checks to see if its updated. If its updated, stop X, stop gdm, run the nvidia installer, then restart gdm. Not rocket science. But my question is, is their another option? Is anyone aware of a work around for the nvidia restricted drivers and what difference their could be between them and the official nvidia drivers and why the restricted drivers from ubuntu fault and say no nvidia card found on system, when the regular drivers from nvidia work just fine. Same version and everything.

Thanks for any suggestions you may have.

Also note his connection is too slow for me to access it though anything but ssh. We don't live close enough for me to have direct access so this.
Also note using the "nv" module is not an option, need glx support and the offical "nvidia" module.

Easier then I thought. You can extract the installation file, then add the argument -s to assume yes and accept agreement and it will automatically setup and install.

---

