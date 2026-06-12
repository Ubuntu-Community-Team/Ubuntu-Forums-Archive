---
title: "Asus Zenbook fan not reaching high speeds"
date: 2024-07-13
forum: Hardware
---

### Post by raif on 2024-07-13
My laptop fans do not go above a slow speed about 2000rpm, even when the processor is under a great load and temperatures go over 90C. This is causing damage and restricting what I can use my laptop for. I know the fans can go much faster from testing then in the BIOS utility. I'm using Linux 6.8.0-38-generic on 24.04 on a Zenbook with AMD Ryzen & integrated graphics. 

Steps already tried:

Installed lm-sensors and fancontrol. 

pwmconfig
But "There are no pwm-capable sensor modules installed"

[https://askubuntu.com/questions/1254364/how-to-control-fans-on-an-asus-laptop](https://askubuntu.com/questions/1254364/how-to-control-fans-on-an-asus-laptop) 
But I can't find a pwm1_enable file anywhere

[https://ubuntuforums.org/showthread.php?t=2486401&highlight=asus+fan](https://ubuntuforums.org/showthread.php?t=2486401&highlight=asus+fan)
[https://gitlab.com/asus-linux/asusctl](https://gitlab.com/asus-linux/asusctl)
But the utilities for available for Asus laptops seem focused on ROG gaming models, not Zenbooks.


Any help greatly appreciated!

---

### Post by Yellow Pasque on 2024-07-14
Asusctl is probably what you want:
[https://gitlab.com/asus-linux/asusctl/-/blob/main/data/asusd.rules?ref_type=heads](https://gitlab.com/asus-linux/asusctl/-/blob/main/data/asusd.rules?ref_type=heads)

The problem with asusctl is that it often demands you use the latest version of everything. IIRC, it said it only supported kernel 6.10, even before 6.10-rc1 was available.

---

### Post by raif on 2024-07-15
Great spot, many thanks indeed! 

See what you mean about the demands! How serious are they, e.g. 6.10 only seems to have been fully released hours ago?! Hope it means just that some features won't work, rather than causing any issues.
 [https://www.omgubuntu.co.uk/2024/07/linux-kernel-6-10-new-features]("https://www.omgubuntu.co.uk/2024/07/linux-kernel-6-10-new-features")

Also there is now a lack of information on Asusctl about how to install on Ubuntu, unfortunately. Any pointers appreciated.

> 
Ubuntu, Popos (unsuported):
instructions removed as outdated

---

### Post by Yellow Pasque on 2024-07-22
> **raif said:**
> Any pointers appreciated.

These are the dependencies you'll need:
```
sudo apt install build-essential cargo cmake libclang-17-dev libinput-dev libseat-dev libgbm-dev libxkbcommon-dev libsystemd-dev libdrm-dev libexpat1-dev libpcre2-dev libudev-dev libzstd-dev libgtk-3-dev
```
If it doesn't build or work correctly, good luck with that. I can get it to build, but all it ever does is crash in a VM, even a basic "asusctl --help". I don't have an Asus laptop, so maybe it's supposed to crash. I don't know.

---

### Post by raif on 2024-07-29
Thanks but afraid I'd need other fuller instructions. This goes beyond my technical knowledge, and it seems to require nearly 1Gb of additional disk space. So will keep looking for more light weight alternatives.

---

### Post by Yellow Pasque on 2024-07-30
> **raif said:**
> Thanks but afraid I'd need other fuller instructions..

The rest is the the same as  the build instructions for other distros. All you do is:
```
make
sudo make install
```

---

