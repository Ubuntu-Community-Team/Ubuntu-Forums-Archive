---
title: "the USB Serial Module in kernel 2.6.28-13-generic, How To"
date: 2009-06-21
forum: Hardware
---

### Post by zakur0 on 2009-06-21
I'm trying to configure the usb serial module for kernel  2.6.28-13.

I could do it with the older kernel, which is kernel 2.6.28-11-generic.

To /boot/grub/menu.lst, I added usbserial.vendor=0x1c9e, and usbserial.product=0x6061, like following:


/boot/grub/menu.lst```

--snip--
title       Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        43c8028b-a7d0-453a-bea0-ee259aaa246fe
kernel      /boot/vmlinuz-2.6.28-11-generic root=UUID=43c8028b-a7d0-453a-bea0-ee259aaa246f ro quiet splash usbserial.vendor=0x1c9e usbserial.product=0x6061
initrd      /boot/initrd.img-2.6.28-11-generic
quiet
--snip--
```However, when I do the same for the kernel 2.6.28-13-generic, I get these error messages during booting Ubuntu with Grub Loader:

Unknown boot option `usbserial.vendor=0x1c9e': ignoring
Unknown boot option `usbserial.product=0x6061': ignoring

So, how should I configure usb serial module in kernel 2.6.28-13 ?

Thank you.

p.s. the purpose is to use the usb_modeswitch command to use a mobile broadband modem, which name is D11LC.

---

### Post by GeorgeVita on 2009-06-22
Hi **zakur0**,
usbserial is an external driver again (as many users asked)!

From kernel **2.6.28-13-generic** you can use it as in the past:

**sudo modprobe usbserial vendor=0x1c9e product=0x6061**

(reference: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002))

Regards,
George

---

