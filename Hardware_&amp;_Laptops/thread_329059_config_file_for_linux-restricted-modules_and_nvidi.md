---
title: "config file for linux-restricted-modules and nvidia"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by lcaley on 2006-12-31
Hello. I was having trouble getting my nvidia drivers to compile when I changed my kernel, but I have gotten them to work all except for a conflict with the linux-restricted-modules packages. If I uninstall the package, my drivers work fine on startup just like they're supposed to. But my wireless drivers, my laptop battery support and I'm sure many other things stop working. With the packages installed, it boots to a shell only, until I recompile and reinstall the drivers. Then it works fine until I log off or reboot. I read on the nvidia site that there is a config file for the linux-restricted-modules packages that I can add a line to that will only exclude the nvidia module from the package, but the config file is not where the guide says it is, and I can't find it anywhere. I'm running Edgy on a hp dv5000 laptop with a nvidia geforce go 7400 graphics card, with the 2.6.17-10-generic kernel. 

Thanks any help.

---

### Post by lcaley on 2006-12-31
Never mind. I got it, thanks for the read though.

---

