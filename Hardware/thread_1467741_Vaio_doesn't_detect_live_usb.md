---
title: "Vaio doesn't detect live usb"
date: 2010-05-01
forum: Hardware
---

### Post by Twisted871 on 2010-05-01
Hey all, I am trying to install Ubuntu 9.10 on my Sony Vaio VGN-NR430E using a live USB. I currently have Windows XP and Mac OS installed on the laptop. My computer can't seem to detect the USB, as it does not appear in my boot menu. I've tried using this tutorial ([http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)) and this one( [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)). Both times resulted in my computer completely ignoring the flash drive during boot up.
According to my BIOS I should be able to boot from USB. My flash drive is using USB 2.0 and is 2GB in size. I've tried googling to see if this is a common problem but I have not been able to find anything. Do you guys have any suggestions?

---

### Post by dino99 on 2010-05-01
> **Twisted871 said:**
> Hey all, I am trying to install Ubuntu 9.10 on my Sony Vaio VGN-NR430E using a live USB. I currently have Windows XP and Mac OS installed on the laptop. My computer can't seem to detect the USB, as it does not appear in my boot menu. I've tried using this tutorial ([http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)) and this one( [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)). Both times resulted in my computer completely ignoring the flash drive during boot up.
According to my BIOS I should be able to boot from USB. My flash drive is using USB 2.0 and is 2GB in size. I've tried googling to see if this is a common problem but I have not been able to find anything. Do you guys have any suggestions?

questions:
- into bios, is usb activated ?
- do plug the stick after or before booting ?

test the result with lsusb

you can do : sudo dpkg-reconfigure usbutils

---

