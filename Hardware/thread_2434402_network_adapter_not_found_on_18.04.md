---
title: "network adapter not found on 18.04"
date: 2020-01-05
forum: Hardware
---

### Post by mark allyn on 2020-01-05
Hello everyone,

Yesterday I finally successfully installed ubuntu 18.04 on a usb flash drive.  Everything works fine except networking.  According to "system settings" window the network adapter is not being found.  Any suggestions would be welcome.

Regards,
Mark Allyn

---

### Post by TheFu on 2020-01-05
If the card isn't found, that means there is a missing driver.  Some commands to help determine the network devices on the system:

```
sudo lspci -vk |egrep --after-context=8 'Ethernet|Network'
sudo lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
sudo lshw -C network
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet 
```

Note that PCI and USB adapters will need different commands.

---

