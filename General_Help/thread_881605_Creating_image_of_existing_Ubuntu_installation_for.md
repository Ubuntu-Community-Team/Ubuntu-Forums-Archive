---
title: "Creating image of existing Ubuntu installation for use with VMware"
date: 2008-08-06
forum: General Help
---

### Post by ShredderLM on 2008-08-06
Hello,

how can I create a image (for the use in VMware) of an existing Ubuntu installation?

Regards, ShredderLM

---

### Post by zvacet on 2008-08-06
[Here]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

---

### Post by LanceRushing on 2008-08-06
A side note:

I have a "clean install" of ubuntu on our VMWare ESX server.

I use **vmkfstools -i** to clone the clean install to new machines.

However, after copying/clone eth0 doesn't show correctly.

I got eth0 to work by doing the following:

```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo reboot
```

Also I went back and removed the 70-persistent-net.rules from my gold source used for cloning.

---

