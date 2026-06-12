---
title: "Scanning How To Proposed Update"
date: 2013-12-18
forum: Hardware
---

### Post by JDorfler on 2013-12-18
I have a proposed update to [ScanningHowTo]("https://help.ubuntu.com/community/ScanningHowTo") for networking an HP Photosmart 7520 without installing .

With Ubuntu 13.04 64 all I did was add the ip address of my printer to saned's net.conf ```
sudo nano /etc/sane.d/net.conf
``` and ```
sudo service saned restart
``` and I was scanning away.  HPLIP drivers were already installed however from a previous USB HP Printer install.

---

### Post by JDorfler on 2013-12-20
Further testing reveals there is no need to ```
sudo service saned restart
```.

---

