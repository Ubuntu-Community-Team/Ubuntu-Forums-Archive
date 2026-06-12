---
title: "HP DV4 - Wireless"
date: 2010-07-06
forum: Hardware
---

### Post by nconceicao on 2010-07-06
I am having a hell of a problem, I have a HP DV4 Laptop.. 
When I pop in my live CD the system boots and it pops up the restricted drivers I am able to accept them and wifi works perfectly.

now

if I install ubuntu 10.04 and reboot no wifi is present and the restricted drivers do not come up.. I am left stranded..

Why or how can I resolve this?

"Broadcom" obviously lol..

DV4 
Model 1228ca

Thank You

---

### Post by lidex on 2010-07-06
Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless")

Find your wireless model with this command in a terminal:
```
lspci
```

---

### Post by Yellow Pasque on 2010-07-06
Use this to see if the driver is already installed/loaded:
```
sudo lshw -C network
```

Also, make sure the necessary packages are installed for restricted drivers:
```
sudo apt-get install bcmwl-modaliases jockey-gtk
```
Then look in System -> Administration -> Hardware Drivers

---

