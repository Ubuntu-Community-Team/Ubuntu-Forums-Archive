---
title: "Bluetooth fix for 12.04"
date: 2012-07-13
forum: Hardware
---

### Post by AbramS on 2012-07-13
Bluetooth not working. Lenovo G Series. Don't think it's specific to any hardware.
Has anybody else figured out how to get it working?

Thank you,
Sam

---

### Post by davidbilla on 2012-08-29
Hi, I have a Lenovo Y570 running Ubuntu 12.04 and I think I may have the same problems too. Wireless works but I can't enable bluetooth in System Settings -> Bluetooth. It stays disabled.

---

### Post by cortman on 2012-08-29
Hi, have you checked out [this documentation]("https://help.ubuntu.com/community/BluetoothSetup")?

---

### Post by davidbilla on 2012-08-29
Hi, thanks for the quick reply and the link! I found a similar solution [here.]("http://askubuntu.com/questions/141158/bluetooth-not-really-turning-on-on-a-sony-vaio-vpceg")

It appears to be a linux issue, not specific to Ubuntu - [check this.]("https://bugs.launchpad.net/ubuntu/+source/bluez-tools/+bug/984299")

This is how I got it working - luckily, it so happens that I have a dual-boot system (it's more like I hadn't removed the other OS yet!). I booted into windows and turned the bluetooth on and restarted the system to boot into ubuntu... now it works!

EDIT: It doesn't work if the h/w wireless switch is turned off during bootup. I had to make sure that the wireless switch was on before booting into ubuntu. So, hopefully it works for systems without dual-boot too. Unless bluetooth drivers for windows are for some reason necessary for it to work in ubuntu.

---

