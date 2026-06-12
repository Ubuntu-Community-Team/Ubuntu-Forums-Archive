---
title: "Creating udev rules symlink"
date: 2010-11-19
forum: Hardware
---

### Post by di3gopa on 2010-11-19
Hi everyone, I am trying to create a udev rule, i have a device that it is mounted by default on /dev/hidraw0 but i need it on /dev/hiddev0, i created a simple rule to make a symlink on /etc/udev/rules.d/10-local.rules -> KERNEL="hidraw0", SYMLINK="hiddev0" but it is not working, any advice? thanks!

My dmesg | tail
```
[123106.000198] usb 5-3: new low speed USB device using ohci_hcd and address 62
[123106.218432] input: Keytec Magic Touch USB as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input41
[123106.218707] generic-usb 0003:0664:0305.0020: input,hidraw0: USB HID v1.00 Device [Keytec Magic Touch USB] on usb-0000:00:13.0-3/input0

```

Thanks!

---

### Post by dino99 on 2010-11-19
[http://www.noob2geek.com/how-to/how-to-create-hard-and-symbolic-links-in-ubuntu/](http://www.noob2geek.com/how-to/how-to-create-hard-and-symbolic-links-in-ubuntu/)

---

### Post by di3gopa on 2010-11-19
I created a simple symlink before but it didnt worked because i need it at boot time so the driver can load.

Thanks

---

