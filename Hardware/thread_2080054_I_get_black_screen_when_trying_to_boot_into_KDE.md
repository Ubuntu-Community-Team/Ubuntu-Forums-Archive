---
title: "I get black screen when trying to boot into KDE"
date: 2012-11-03
forum: Hardware
---

### Post by gizmobay on 2012-11-03
I had a GeForce 7200 PCIe car using the nouveau drivers without issue. The card all of a sudden started making a bad noise from the fan. I had a GeForce FX 5200 PCI laying around so I swapped the cards out. I can boot into Gnome no effect but when I try KDE I get a black screen. Through grub2 I can boot into recovery mode and the failsafe mode to get back to kde. This isn't ideal since I have to rearrange my panels every boot and I can't reboot without doing this all over again. Can someone point me in the right direction?

---

### Post by whatthefunk on 2012-11-03
Try editing you /etc/dfault/grub file.  Find the line 
```
GRUB_CMDLINE_LINUX_DEFAULT='quiet splash'
```
and change it to
```
GRUB_CMDLINE_LINUX_DEFAULT='quiet splash nomodeset'
```

Also make sure you are using the nvidia driver.  You can check by going to System > Additional Drivers.

---

### Post by gizmobay on 2012-11-03
Thanks this fixed my problem. I am now back up and running.

---

