---
title: "Install USB Printer Canon i-sensys MF4780W on Ubuntu 18.04"
date: 2020-03-06
forum: Hardware
---

### Post by smitla on 2020-03-06
Hi

Install USB Printer Canon i-sensys MF4780W on Ubuntu 18.04

Please can any one assist in this

---

### Post by slickymaster on 2020-03-06
Thread moved to **Hardware** for a better fit

---

### Post by brian_p on 2020-03-06
[https://wiki.debian.org/Canon](https://wiki.debian.org/Canon)

---

### Post by smitla on 2020-03-06
> **brian_p said:**
> [https://wiki.debian.org/Canon](https://wiki.debian.org/Canon)


Brian thx but not working.

This is the problem.

```
ejk@ejk-MS-7788:~$ cd linux-UFRII-drv-v510-uken/32-bit_Driver/Debian
ejk@ejk-MS-7788:~/linux-UFRII-drv-v510-uken/32-bit_Driver/Debian$ sudo apt install ./cndrvcups-common_4.10-1_i386.deb ./cndrvcups-ufr2-uk_3.70-1_i386.deb 
[sudo] password for ejk: 
Reading package lists... Done
E: Unsupported file ./cndrvcups-common_4.10-1_i386.deb given on commandline
E: Unsupported file ./cndrvcups-ufr2-uk_3.70-1_i386.deb given on commandline
```

---

### Post by CelticWarrior on 2020-03-06
[https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/laser/laserbase_mf_series/i-sensys_mf4780w.html?type=drivers&driverdetailid=tcm:14-1506758](https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/laser/laserbase_mf_series/i-sensys_mf4780w.html?type=drivers&driverdetailid=tcm:14-1506758)

This is the link to the newest drivers.
Download to your Downloads folder, for example. Right-click and "Extract here". The file you need will then be in the following path: 

/Downloads/linux-UFRII-drv-v510-uken-19/linux-UFRII-drv-v510-uken/64-bit_Driver/Debian 

It's a .deb file that can be installed like any other. The easiest option is double-clicking that will open the "app store", click install. Done.

Alternatively you can use one of the methods described in the Debian link in the previous post.

**Method 1:**

```
cd ~/Downloads/linux-UFRII-drv-v510-uken-19/linux-UFRII-drv-v510-uken/64-bit_Driver/Debian
sudo apt install ./cnrdrvcups-ufr2-uk_5.10-1_amd64.deb
```


[B]Method 2:


[/B]```
cd ~/Downloads/linux-UFRII-drv-v510-uken-19/linux-UFRII-drv-v510-uken
sudo bash install.sh
```


All the methods above assume you're downloading and extracting to a Downloads folders. Adjust if necessary (e.g. if your OS is in another language then the downloads folder probably has a different name).
Also assumed is that you're running a **64-bit** OS so you want to installk 64-bit drivers, not the one that you apparently downloaded while I was composing this post.

---

### Post by CelticWarrior on 2020-03-06
> **smitla said:**
> Brian thx but not working.

This is the problem.

ejk@ejk-MS-7788:~$ cd linux-UFRII-drv-v510-uken/32-bit_Driver/Debian
ejk@ejk-MS-7788:~/linux-UFRII-drv-v510-uken/32-bit_Driver/Debian$ sudo apt install ./cndrvcups-common_4.10-1_i386.deb ./cndrvcups-ufr2-uk_3.70-1_i386.deb 
[sudo] password for ejk: 
Reading package lists... Done
E: Unsupported file ./cndrvcups-common_4.10-1_i386.deb given on commandline
E: Unsupported file ./cndrvcups-ufr2-uk_3.70-1_i386.deb given on commandline

Wrong driver, probably. This is the 32-bit driver. Do you really have a 32-bit OS? Hopefully not...
And then your path is all wrong  - ./cndrvcups-ufr2-uk_3.70-1_i386.deb twice - hence the error message .

---

### Post by smitla on 2020-03-12
> **CelticWarrior said:**
> Wrong driver, probably. This is the 32-bit driver. Do you really have a 32-bit OS? Hopefully not...
And then your path is all wrong  - ./cndrvcups-ufr2-uk_3.70-1_i386.deb twice - hence the error message .

Hi

Install the printer but if i print a test page it start the printer but did not print.

Thx

L Smit

---

