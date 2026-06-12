---
title: "SD card reader"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by dmery on 2006-06-12
Hi,
I have a laptop HP Pavilion zv6015 AMD-64 +3500
Dapper is runing ok on it but mi SD card reader is not working.:confused:       
Somebody knows how to set this device ?
I know that Gentoo  is working fine with SD card reader on HP.
I appreciate some help
Regards,
dmery:p

---

### Post by guano on 2006-06-12
I use Dapper on a HP DV-4130. SD reader works fine.

---

### Post by arkTIK on 2006-06-14
I'm using a Toshiba Satellite M50 with a built-in mulit-card-reader and have XUBUNTU 6.06 installed.
The only thing I did to make the SD card reader to work was to add the line
/dev/mmcblk0    /media/sdcard     auto     noauto,rw,user,exec,sync   0 0
to /etc/fstab and use the "Mount Devices" xfce4 applet to mount/unmount the device.

lshw [list hardware] shows that the PCI device [Host Bridge - PCI Bridge - Generic System Peripheral] uses the sdhci driver.
When I insert a card the device /dev/mmcblk0p1 is created, hence above fstab-entry. Another good tool to verify that the device works is hal-device-manager.
To auto-mount you may use ivman or gnome-volume-manager (I'm not too sure what the equivalent for KDE is...).

Good luck

---

### Post by arkTIK on 2006-06-14
The correct fstab entry should read:
/dev/mmcblk0p1 /media/sdcard auto noauto,rw,user,exec,sync   0 0

---

### Post by dmery on 2006-06-14
Thanks Artik and Guano for answering,:D      

I have the driver sdhci but I do not to set the automonter in Gnome. I have experience with Gentoo and KDE. This is my first time with Ubuntu and sometime I am lost !!!!!
I think that using xfce desktop is so diferent to use Gnome. With Xfce desktop you need to manually mount all usb devices and maybe the same for SD card reader ? But with Gnome I think is a little diferent because it is using hal, ivman, pmount and udev. I know how to handle this drivers with Gentoo but with Ubuntu I am a little bit confused about that. Do you know where can I get a good "howto" ? ....or maybe you have more detailed directions to set it.
Thanks in advance
Regards,
dmery:p

---

