---
title: "Bluetooth connection"
date: 2009-07-14
forum: Hardware
---

### Post by shang1 on 2009-07-14
Hello,
I am currently in need of using a bluetooth device for my computer. However I do not wish to purchase a dongle for this use.

I have a nokia N95 which has bluetooth, I am wondering is it possible to use my bluetooth via my ubuntu machine. I have tried numerous google seaches but none seem to meet my needs.

The device connects to my computer fine via the USB cable:
```
Bus 004 Device 004: ID 0421:006d Nokia Mobile Phones 

```

I edited my grub boot loader:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b48dc3b4-c0a8-4c73-87d8-38207ab768f5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b48dc3b4-c0a8-4c73-87d8-38207ab768f5 ro quiet splash
usbserial.vendor=0x0421 usbserial.product=0x006d
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

However I have no idea where to go from here as no one (I can find) has done this before.. Any help would be greatly appreciated.
Thanks.

---

