---
title: "Asus wireless N10"
date: 2011-03-17
forum: Hardware
---

### Post by granul on 2011-03-17
I'm using Ubuntu 10.10 64bit, and i'm using a usb Asus wireless N10 to acess internet, I mange to make it work with the folowing line:


sudo ln -s /lib/firmware/RTL8192SE/ /lib/firmware/RTL8192SU
sudo modprobe -r r8192s_usb
sudo modprobe r8192s_usb 


The problem is tha I losse it every time I reboot, I have to write this again every time, **sudo modprobe r8192s_usb**.

---

### Post by mikewhatever on 2011-03-17
Just add your module, r8192s_usb, to /etc/modules, and it will autoload every time you boot.

---

### Post by granul on 2011-03-17
Thank you it works

---

