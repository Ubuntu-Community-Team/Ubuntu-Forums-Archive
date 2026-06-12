---
title: "Broadcom 4328 rev03 (HP TX1410US)"
date: 2008-04-24
forum: Hardware
---

### Post by adewolf on 2008-04-24
Here are instructions to get the Broadcom 4328 rev03 working:
1. Make sure the ndiswrapper-utils is installed
2. mkdir ~/bcm43xx;cd bcm43xx
3. wget [http://myspamb8.googlepages.com/R174291-pruned.zip](http://myspamb8.googlepages.com/R174291-pruned.zip)
4. unzip R174291-pruned.zip
5. sudo ndiswrapper -i bcmwl5.inf
6. ndiswrapper -l
should show:
bcmwl5 : driver installed
   device (14E4:4328) present (alternate driver: ssb)
7. sudo depmod -a
8. sudo modprobe ndiswrapper
9. sudo cp /etc/network/interfaces /etc/network/interfaces.orig
10. echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
11. sudo ndiswrapper -m
12. echo 'ndiswrapper' | sudo tee -a /etc/modules
13. echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
14. sudo vi /etc/modprobe.d/ndiswrapper  add the following line:
install ndiswrapper modprobe -r ohci-hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci-hc

Works in 8.04 as well

Alex

---

### Post by enginuysal on 2009-01-08
> **adewolf said:**
> 
6. ndiswrapper -l
should show:
bcmwl5 : driver installed
   device (14E4:4328) present (alternate driver: ssb)


What if it shows only;
```
bcmwl5 : driver installed
```

Would that mean that my network adapter is physically corrupted?

Thanks in advance

---

