---
title: "Adb not Read my android device under lubuntu 14.04 under window succes"
date: 2014-09-14
forum: Hardware
---

### Post by rofik on 2014-09-14
I already create 51-android.rules in etc/udev/rules.D/ and give a rwx permission , , and i create lsusb , give produc id and vendor id , , its 2207:0010 , but there no name or detail , my tablet is rockchip 2918 board . . .

Here my script : subsystem="usb", ATTR{idVendor}=="2207", ATTR{idProduct}=="0010", MODE="0666", GROUP="plugdev"

sudo udevadm trigger && sudo reboot


sudo adb devices

lubuntu 14

---

