---
title: "ati intel switchable graphics"
date: 2012-06-02
forum: Hardware
---

### Post by farzadbashtani on 2012-06-02
I have a hp probook 4530s with ati and intel switchable graphics.
I've installed amd catalyst control center (ati driver) which is the official driver by the way. it let me to choose between the gpus.
by default ubuntu uses my ati gpu. I want to use the intel instead due to some reasons. after choosing intel in catalyst control center it asks me to restart the system. after restarting, ubuntu dont boot and shows an error which indicates that it does not recognize my graphic card (intel).

I think making the Xorg reconfigure itself again would help the problem but I dont know how to do it.

would you please help me with this?

---

### Post by N0oki3 on 2012-06-06
This might help:
edit /etc/default/grub
> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force intel.nomodeset=1"

and update it
>  update-grub

---

### Post by QIII on 2012-06-06
Try this:

[Hybrid Graphics Works](http://ubuntuforums.org/showthread.php?t=1930450)

---

