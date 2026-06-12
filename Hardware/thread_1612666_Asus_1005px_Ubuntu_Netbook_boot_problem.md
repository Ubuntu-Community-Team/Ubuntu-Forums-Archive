---
title: "Asus 1005px Ubuntu Netbook boot problem"
date: 2010-11-03
forum: Hardware
---

### Post by jahman123 on 2010-11-03
Hello,

I'm all new to the Ubuntu world and would like to discover it by installning Ubuntu Netbook on my Asus eee 1005px. 

I started off by downloading it from the website and whit Universal USB Installer i successfully got the files on my usb-drive. 

But here is the problem, when i jump right into BIOS (F2) and change the Boot Device Priority to the usb-drive and restart the computer i keep finding myself booting into "Windows 7 Starter" (The standard OS on my laptop). 

So i tried as well pressing the (ESC) key and change the boot device from there but nothing changes and i'm getting redirected to Windows 7 Starter once more that are installed on the hard drive. 

I'm at the moment clueless about where to move on from where and asking as last hope for some advice to help me get this done.

---

### Post by anagor_lv on 2010-11-12
I suppose, the netbook's BIOS identifies your USB as a non-bootable device. This may happen if the ISO image was incorrectly recorded on the USB stick. Try recording it again.

---

### Post by anagor_lv on 2010-11-14
I am also going to install Ubuntu on ASUS Eee PC 1005PX.
Changing the Boot Priority in BIOS was not enough. I got redirected to Windows 7.
I managed to boot Ubuntu by pressing ESC during bootup and choosing the USB drive as a boot device.
[http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1000H/XP&id=20090507154557268&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1000H/XP&id=20090507154557268&page=1&SLanguage=en-us)

Have you disabled the Boot Booster in your netbook's BIOS? If you don't, you cannot boot from USB.

---

