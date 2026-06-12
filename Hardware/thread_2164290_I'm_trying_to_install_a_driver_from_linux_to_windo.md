---
title: "I'm trying to install a driver from linux to windows."
date: 2013-07-31
forum: Hardware
---

### Post by EKx6kpG on 2013-07-31
Hi all,
    I have a desktop i'm running two hard drives off of. I recently installed my driver software for a wireless card on the disk running Ubuntu. Sadly I can't find the disk again, so my question(s) are; is it possible to make windows search the other drive for the driver info and if so how? It should be noted I can access the windows drive from Linux, but not vice versa. Thanks in advance.

---

### Post by SweetAurora on 2013-07-31
No. Windows Drivers and Linux Drivers are totally different things. You can't use drivers from one on the other. Sorry, but you will have to find the driver online. If your PC has no connection because it runs off the Wifi, use your phone's internet to download the driver from the manufacture's site.

---

### Post by EKx6kpG on 2013-07-31
Thanks! The only other problem I have, may as well post it here, is I tried to use a bridged connection from my laptop to the desk and it wouldn't pick it up for some reason. I naturally then tried just going off the router and same problem. Any ideas?

---

### Post by Yellow Pasque on 2013-07-31
Which driver are you looking for - the linux one or the windows one?
It would really help to know what chipset your wireless card has:
```
lspci
lsusb #if it's a USB card
```

---

