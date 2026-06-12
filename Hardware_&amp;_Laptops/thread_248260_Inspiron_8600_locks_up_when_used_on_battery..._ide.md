---
title: "Inspiron 8600 locks up when used on battery... ideas?"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by 2shanfernando on 2006-08-31
Hi,

Recently switched to Ubuntu on an old Inspirion 8600 I had, installed Ubuntu with ResiezerFS and everything's cool apart from not being able to boot a X when running on batteries.

On power/AC its fine, i'm not using the Mesa Drivers (the default ATI Ones) and had a bitch of a time getting them to work (Mesa always came back), is there a way of getting a log of the boot process before i login??

In recovery mode I can manually go into X (startx) fine but if I let it boot the non-recovery mode it stalls straight after the intial boot sequence (where the Login screen should show)... I'm still very new to this so if you need logs etc please post what comamnds i need to get:-)

Stats:
Inspiron 8600
PentiumM 2Ghz
ATI Radeon 9600T

Thanks,

---

### Post by 2shanfernando on 2006-08-31
OK i successfully installed the latest ATI drivers (ati-driver-installer-8.28.8) but no luck on booting Ubuntu with battery power...

---

### Post by 2shanfernando on 2006-09-01
OK sorted it out.

In the Insprion 8600 I disabled the onboard Wireless and the internal modem which now seems to allow it to boot from battery...

---

