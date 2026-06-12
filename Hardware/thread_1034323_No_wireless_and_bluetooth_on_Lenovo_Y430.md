---
title: "No wireless and bluetooth on Lenovo Y430"
date: 2009-01-08
forum: Hardware
---

### Post by javaman1909 on 2009-01-08
Hi all.

I have installad Ubuntu on my new Lenovo Y430, everything seems to work fine except wireless and bluetooth. I cant scan any wireless around me, and the signal light seems not to turn wireless on. In Windows Vista, if I want to turn wireless on, I first have to switch the device on, and activate a software, then the wireless light turn on. In Ubuntu, even when I switch the device on, I dont know how to enable wireless or I dont know if Ubuntu installed my wireless correctly. Similar to bluetooth.

Anyone has installed ubuntu on lenovo y430 please help me, all helps are appreciated.

Thanks.

---

### Post by ASchweitzer on 2009-01-08
Looks like you don't have drivers for your wireless hardware. If you could, run this in terminal and post the output:
```
lspci | grep Ethernet
```
This will give you an output of what your wireless controller is detected as, which you can then post here and search for drivers for. Using this hardware name will give you much better search results.

Side note: the *lspci* command lists pci devices in your machine, similarly to how *ls* will list contents of your current directory and *lsusb* will list usb devices and ports. The *grep Ethernet* part uses the *grep* command to filter out any content that doesn't contain the word "Ethernet". You'll see what I mean if your compare the output of *lspci* to that of *lspci | grep Ethernet*

---

