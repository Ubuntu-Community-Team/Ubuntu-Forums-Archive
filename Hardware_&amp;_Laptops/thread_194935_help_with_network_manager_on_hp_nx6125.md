---
title: "help with network manager on hp nx6125"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by bato on 2006-06-12
Hello,

I have a hp compaq nx6125 with Turion AMD64 processor. I have upgraded to dapper from breezy. Wireless works well with ndiswrapper but network manager dosen't work properly. It shows to me only wired connection but no wireless.

I edited /etc/modprobe.d/blacklist with balcklist bcm43xx

Then I have done:

```
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

I tried with bcm43xx driver too follow this

> Wireless works with bcm43xx driver and ndiswrapper. For bcm43xx you have to download the fwcutter 'apt-get install bcm43xx-fwcutter' and extract the firmware from the .sys file 'bcm43xx-fwcutter bcmwl5.sys' and copy the *.fw files to /lib/firmware/$(uname -r). For every version of kernel you have to do this.

form [https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6125](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6125)

In this case the network card is recognized, network manager seems works but I can't connect.

Any ideas? :-k

---

