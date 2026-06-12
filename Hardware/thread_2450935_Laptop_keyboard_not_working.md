---
title: "Laptop keyboard not working"
date: 2020-09-23
forum: Hardware
---

### Post by mrutyunjayagadanayak on 2020-09-23
I am on Acer 215 series laptop using ubuntu 18.04. 
Today after a reboot my laptop keyboard stopped working but i can use onscreen keyboard and usb keyboard.
Both touch screen and mouse also working.
I can confirm that the laptop keyboard is fine since i can use it from ubuntu live CD.

As for troubleshooting i tried changing the layout and installing xserver-xorg-input-all to no change 

Any advice would be appreciated.

---

### Post by mrutyunjayagadanayak on 2020-09-24
After searching sometime i found that the kernel newer then 5.4.18 are having a weird bug that causes this keyboard issue.
I used grub-customizer to make a 5.3 kernel my default boot and the issue is gone. 
This is not a permanent solution but for now it will do since this is my work laptop.

---

### Post by mrutyunjayagadanayak on 2020-09-24
Anyone has any permanent solution for this please tell me

---

