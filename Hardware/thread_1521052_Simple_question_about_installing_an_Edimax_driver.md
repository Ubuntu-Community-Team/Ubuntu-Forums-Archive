---
title: "Simple question about installing an Edimax driver"
date: 2010-06-30
forum: Hardware
---

### Post by GoldenAxe on 2010-06-30
Hi, experts of the Ubuntu netherworld,

I'm trying to install an Edimax wireless card. I've got a question relating to Step 5.3 in the official instructions from Edimax, which I can't figure out. **Where is the "Os/linux" directory in Ubuntu?**


Here are the instructions:
> 
Step 1: Find out your kernel version (The kernel v2.6 is used in this example)

$ uname -r



Step 2: Make computer up to internet first, and download gcc packet,

$ apt-get install build-essential



Step 3: Untar driver

$ tar –zxvf 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar

$ cd 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar


Step 4: Compile driver source code

$ sudo make



Step 5: load driver


5.1

Create a directory

$ sudo mkdir /etc/Wireless/

$ sudo mkdir /etc/Wireless/RT2860SAT/


5.2

Copy configuration files

$ sudo cp RT2860STA.dat

/etc/Wireless/RT2860STA/RT2860STA.dat


5.3 load driver, **go to “os/linux/” directory.**

$sudo insmod rt2860sta.ko

$sudo ifconfig ra0 up


---

### Post by Yellow Pasque on 2010-06-30
You shouldn't need to cd to the directory. Just:
```
sudo depmod -a
sudo modprobe -v rt2860sta
```

---

