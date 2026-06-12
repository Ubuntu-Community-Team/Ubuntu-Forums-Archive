---
title: "WiFI connected but cant get online."
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by ccfromnj on 2009-05-26
I have a Dell Vostro 1000 and a spare harddrive. 

I burned and installed a Jaunty CD, no problems.
I boot up, install the suggested Broadcom Drivers, and reboot, no problems.

At this point after I log in, and connect to WiFi (Which I do with no problems), Ubuntu tells me its connected but no applications can get online (Fire Fox, Synaptic, ect). 
I only have Wifi Access currently, that Window$ uses with no problems ( I gotta keep that for work :( ).

 Its not a access point log on issue. I get an IP address via DHCP

I am sure that I am doing something wrong, Can someone please point me in the right direction ?

Thank you

[email]ubuntu@ccfromnj.com[/email]

---

### Post by 34m0 on 2009-05-29
I got a variant of this on another thread, and it is working for me for with jaunty on a dell vostro 1000



sudo apt-get install linux-backports-modules-jaunty

sudo modprobe -r iwl3945
sudo modprobe iwl3945

---

### Post by ccfromnj on 2009-05-30
*sudo apt-get install linux-backports-modules-jaunty*


I don't have access to a wired network to be able to run apt-get

Thanks for trying !

---

### Post by donkyhotay on 2009-05-30
Can you ping your wireless access point?
```

ping -c5 <IPaddress.of.access.point>

```

---

