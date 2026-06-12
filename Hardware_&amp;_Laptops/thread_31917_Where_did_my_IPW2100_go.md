---
title: "Where did my IPW2100 go?"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by leezer3 on 2005-05-05
Hi all, 
Just upgraded to Hoary, through the web, after finally solving my partition problems. Now, I've got no IPW2100 (It was eth0), even though it was working perfectly before(I upgraded through it!!). The wireless link icon that was on my taskbar also seems to have been replaced with a general one for eth1, & finally the new connection icon in the networking seems to have gone as well. I need info on how to fix this please.

Thanks!

-Leezer-

---

### Post by luca_linux on 2005-05-05
Try to install the latest firmware and driver from [http://ipw2100.sourceforge.net](http://ipw2100.sourceforge.net) and just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
(Note that any string referring to ipw2200 has to be changed in ipw2100 in your case).

---

### Post by leezer3 on 2005-05-09
Sorry for being a n00b :), but I'm getting this output from the make command:
> 
make -C /lib/modules/2.6.8.1-3-386/build SUBDIRS=/home/christopher/Desktop/ipw2100-1.1.0 MODVERDIR=/home/christopher/Desktop/ipw2100-1.1.0 modules
make: *** /lib/modules/2.6.8.1-3-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

I'm assuming that this means I don't have the kernel source installed, but I've installed kernel-source & kernel-tree, but this makes no difference.

Thanks

-Leezer-

---

### Post by luca_linux on 2005-05-09
As said in the howto thread, you need the packages build essentials and kernel headers.

---

### Post by leezer3 on 2005-05-13
Apologies, now starting to beat my head against a brick wall :D
Installed linux-kernel-headers & build-esssentials, but *still* the same error!

Thanks

-Leezer-

---

### Post by luca_linux on 2005-05-13
Install the package linux-tree-2.6.10 too and type at console the following commands:
```

ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
ln -s /usr/src/linux-source-2.6.10 /lib/modules/2.6.10-5-386/build

```
It should work now.

---

