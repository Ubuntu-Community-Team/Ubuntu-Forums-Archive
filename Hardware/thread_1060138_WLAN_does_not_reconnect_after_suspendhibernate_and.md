---
title: "WLAN does not reconnect after suspend/hibernate and change of router"
date: 2009-02-04
forum: Hardware
---

### Post by athrpf on 2009-02-04
Hey everyone,

I use ubuntu 8.10 (Kernel 2.6.27-11-generic) on my laptop. For my WLAN card (Chipset Atheros 242 5007) I use madwifi-hal-0.10.5.6 version of 2008-09-03, which works perfectly fine, usually. The only problem I have, which is pretty annoying, is that every time I suspend/hibernate the system, and I change the router I connect to (e.g. by going from home to university), the WLAN fails to detect any networks out there. I tried restarting the module with

sudo modprobe -r ath_pci 
sudo modprobe ath_pci

but that didn't work. Is there a fix to this problem?

Thanks a lot!

---

