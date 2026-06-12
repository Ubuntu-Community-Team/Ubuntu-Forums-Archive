---
title: "Installing Ubuntu over network (PXE)??"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by ravagilli on 2006-01-05
please could someone help me, i need to install ubuntu on a laptop with no cdrom, its a toshiba quite new but its small hence no cd drive?

---

### Post by phillyboy on 2006-01-05
Do you have:
[LIST]
[*]Windows already installed on the machine
[*]A highspeed internet connection
[/LIST]

If so, then [this program]("http://sourceforge.net/projects/instlux") would be perfect for you. It basically installs some grub-specific items and setups the Windows boot manager to add an entry that is used to start an Ubuntu installation. When you install the program you can select a Network-based or CDROM-based installation. Hope this helps!

---

### Post by ravagilli on 2006-01-05
i dont have windows already on the machine, but i do have a high speed internet connection. i also have another laptop dual booting ubuntu, and windows xp. but my toshiba (the one without an os) can boot to lan, and i wanted to know if it was possible to read the cdrom, with the ubuntu install disc from my other laptop via the network. i have them connected through a hub, and it says its searching dhcp, during boot then displays missing operating system. i was wondering if i can install it through the other laptop, if it was set up as a server type thing?

---

### Post by stuporglue on 2006-01-05
> i wanted to know if it was possible to read the cdrom, with the ubuntu install disc from my other laptop via the network. i have them connected through a hub, and it says its searching dhcp, during boot then displays missing operating system. i was wondering if i can install it through the other laptop, if it was set up as a server type thing?

Yes you can. It is possible, but I've yet to see a clear tutorial of how to get the whole thing setup. 

From the Ubuntu wiki: 
[https://wiki.ubuntu.com/Installation/LocalNet](https://wiki.ubuntu.com/Installation/LocalNet)
[https://wiki.ubuntu.com/PXEInstall](https://wiki.ubuntu.com/PXEInstall)

Good luck!

---

### Post by ravagilli on 2006-01-06
any one else got any help cos ive tried the other methods on the wiki's and cannot seem to get it to work?????????????

---

