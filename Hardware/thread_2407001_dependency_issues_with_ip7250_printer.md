---
title: "dependency issues with ip7250 printer"
date: 2018-11-28
forum: Hardware
---

### Post by day on 2018-11-28
Hello
I downloaded [printer drivers]("https://www.canon.co.uk/support/consumer_products/products/printers/inkjet/pixma_ip_series/pixma_ip7250.aspx?type=drivers&language=&os=Linux%20(64-bit)") from the Canon UK site, they were last updated in 2012 but as far as I know are the current ones.

I see the following dependency problems:

```
dpkg: dependency problems prevent configuration of cnijfilter-ip7200series:
 cnijfilter-ip7200series depends on libpng12-0 (>= 1.2.8rel); however:
  Package libpng12-0 is not installed.
 cnijfilter-ip7200series depends on libtiff4; however:
  Package libtiff4 is not installed
```

My system (bionic)  has libpng16-16 and libtiff5 installed. Does this mean the drivers are now outdated and unuseable?

Thanks

Dave

---

### Post by CatKiller on 2018-11-28
[This page](http://tipsonubuntu.com/2016/08/14/canon-printer-driver-scangear-mp-ubuntu-16-04/) might help.

---

### Post by Kris_M on 2018-11-28
[https://tutorialforlinux.com/2018/11/20/how-to-install-canon-pixma-ip7250ip7260-driver-on-ubuntu-gnulinux/2/](https://tutorialforlinux.com/2018/11/20/how-to-install-canon-pixma-ip7250ip7260-driver-on-ubuntu-gnulinux/2/)

look at step 2.

---

### Post by day on 2018-11-29
Thanks for responses, unfortunately:

Catkiller's suggestion: 
sudo add-apt-repository ppa:inameiname/stable - no release file so disabled. Looking on  [https://launchpad.net/~inameiname/+archive/ubuntu/stable](https://launchpad.net/~inameiname/+archive/ubuntu/stable) it does not seem to have been updated for a while. 

Kris_M
suggests installs libpng3 but "Unable to locate package libpng3" - current version being libpng16-16. Looking on [https://launchpad.net/ubuntu/+search?text=libpng3](https://launchpad.net/ubuntu/+search?text=libpng3) it seems to be downloadable but I don't know if that would mess up more recent versions or result in a security vulnerability

Thanks

---

### Post by Kris_M on 2018-11-29
Yes, when I run that, lib3 is always missing but printer/scanner then works fine.

---

### Post by day on 2018-12-04
Yes thank you, all working including the wireless which is really useful for me. Just had to go into the printer configuration (which I'd connected by usb cable to use before installing the canon drivers) to change the driver from 'driverless' to 'Canon'

---

