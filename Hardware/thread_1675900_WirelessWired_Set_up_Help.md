---
title: "Wireless/Wired Set up Help"
date: 2011-01-26
forum: Hardware
---

### Post by bugs02 on 2011-01-26
I just installed ubuntu 10.10 on an older Compaq Presario X6000 laptop (dual booting with windows 7).. and I'm having troubles setting up the internet connection.. whether wired or wireless.

Connecting an ethernet chord doesn't change anything... any help would be greatly appreciated :mrgreen:

Thanks

---

### Post by pi/roman on 2011-01-26
Find what network hardware is installed
```
sudo lshw -c network
```See what product it is and look up what driver's it uses online. Check whether the driver's available on your system.
```
modprobe -l | grep -i "product id"
```where product id is a group of letters and numbers from your network hardware name.

Check whether the driver module is already loaded:
```
lsmod
```will show all drivers currently loaded on your system.

---

