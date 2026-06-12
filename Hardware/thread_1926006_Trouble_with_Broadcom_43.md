---
title: "Trouble with Broadcom 43"
date: 2012-02-15
forum: Hardware
---

### Post by danileigh79 on 2012-02-15
I have a laptop with a Broadcom 43 wifi adapter. Every time I start up or reboot my laptop, my wifi driver is not enabled and wifi does not show up in the network settings and I have to use the following commands to re-enable it:

"sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

sudo modprobe -r b43 ssb sudo modprobe b43"

When I use the first command, I am given the response "Cannot open input file wl_apsta-3.130.20.0.o". The rest of the commands work pefectly, and my wifi- enables. 

How can I make my wifi stay enabled permanently without having to use the fwcutter and modprobe commands every time I start or reboot my computer?

---

### Post by wildmanne39 on 2012-02-15
Hi, try this please:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

