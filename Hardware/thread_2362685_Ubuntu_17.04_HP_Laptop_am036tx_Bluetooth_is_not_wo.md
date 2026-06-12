---
title: "Ubuntu 17.04 HP Laptop am036tx Bluetooth is not working"
date: 2017-05-31
forum: Hardware
---

### Post by Albert Ng on 2017-05-31
Dear all, I have a laptop HP Notebook - 14-am036tx, Intel® Core™ i3-5005U (2 GHz, 3 MB cache, 2 cores), 8 GB DDR3L-1600 SDRAM (2 x 4 GB), AMD Radeon™ R5 M430 Graphics (2 GB DDR3 dedicated) Discrete, 14" diagonal HD SVA BrightView WLED-backlit (1366 x 768). I had made up my mind to throw away the windows OS and formatted the laptop to a single OS Ubuntu 17.04 today 29 May 2017. Everything worked except the bluetooth didn't work. The Bluetooth icon shown. When search for new device, it didn't detect any device. Please help and advice. Thanks.

---

### Post by vasa1 on 2017-06-01
Please post the output of```
apt list --installed | grep -i blue
```and```
lsusb |grep -i blue

```by copy/pasting. Don't take a screenshot and upload it to Facebook and then post that link. Thanks.

---

