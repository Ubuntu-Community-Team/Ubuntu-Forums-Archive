---
title: "Installing to SSD; any advice?"
date: 2012-07-24
forum: Hardware
---

### Post by prshah on 2012-07-24
Hello,

I am changing the HDD in my Lenovo S10-3t to a Kingston SSDNow 30GB SATA2 SSD (ref product: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820139162](http://www.newegg.com/Product/Product.aspx?Item=N82E16820139162) )

As I understand it, this is an economy model, but it does claim TRIM support for Win7.

Does that mean TRIM support will be activated in Linux too? Do I have to make any specific partition settings, or mount options, etc?

Current plan: 
[LIST]
[*] Install Ubuntu 12.04 64 bit (fresh)
[*] single partition + swap partition (for hibernate support)
[*] create small ramdisk for /var/log (only).
[*] update /etc/fstab to include ramdisk, and discard,noatime options for /
[*] set vm.swappiness low (10?) in /etc/sysctl.conf
[/LIST]

Any advice? Tech level: intermediate-high.

---

### Post by Redblade20XX on 2012-07-24
Take a look here: [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

- Red

---

