---
title: "Broadcom Wireless Help"
date: 2008-04-30
forum: Hardware
---

### Post by BlueFeast on 2008-04-30
I have read everything i can find online on how to do this, but i cant find anything that works! gah! Right now,when i click on the two screens on the task bar it gives me this 

"- Wired Network
_______________Wireless Networks___________
Connect to Other wireless Network...
Create New wireless Network...
-------------------------------------------
Connect to 802.1X Protected Wired Network....
Manual Configuration" 

when i enter
```
 lspci | grep Broadcom\ Corporation
```
the output is "03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)"

the light that was blue when it was working with Vista is orange. please help?

---

### Post by salocinbake on 2008-05-01
Try this:
Connect yourself to the internet with a ethernet cable, then;
```
sudo apt-get install b43-fwcutter
```

Then reboot.

Hope this help,

If not remove it, ```
sudo apt-get remove b43-fwcutter
```

---

### Post by mringer on 2008-05-23
Having installed b43-fwcutter  & rebooted,  how does one then get it to work?

---

