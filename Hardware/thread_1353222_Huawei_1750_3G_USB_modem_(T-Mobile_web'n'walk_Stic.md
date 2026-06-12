---
title: "Huawei 1750 3G USB modem (T-Mobile web'n'walk Stick V)"
date: 2009-12-12
forum: Hardware
---

### Post by sola on 2009-12-12
This device doesn't work out of the box because Ubuntu handles only the storage part of the stick and ignores the 3g modem part.

With Ubuntu Karmic, I managed to get it work, so I post it here, someone may need it.

Steps (from the command line)



==============================
 Usb-Modeswitch installation
==============================

```

sudo apt-get install usb-modeswitch

```

===========================================
 Usb-Modeswitch config file
===========================================

```

sudo gedit /etc/udev/rules.d/61-huawei_e1750.rule

```The newly created config file opens in gedit (empty). Put this into the file:

```

# T-Mobile Web'n'walk stick V
SUBSYSTEM=="usb", SYSFS{idVendor}=="12d1", SYSFS{idProduct}=="1446", RUN+="/usr/sbin/usb_modeswitch --default-vendor 0x12d1 --default-product 0x1446 --target-vendor 0x12d1 --target-product 0x1001 --message-content 55534243000000000000000000000011060000000000000000000000000000"

```



After a full Ubuntu restart, the device should get properly recognized.

If you remove and re-insert the stick, Gnome NetworkeManager should display a wizzard for configuring the network connection (if you don't have your broadband net connection configured yet)

This is mostly the same with Jaunty but the usb-modeswitch package has to be downloaded and installed separately because it is not in the repositories.





===========================================
Troubleshooting
===========================================
 

Remaining 61-option-modem-modeswitch.rules file
-----------------------------------------------------------
On one of my laptops, I had a file remaining from an earlier installation:
```

/lib/udev/rules.d/61-option-modem-modeswitch.rules 

```This file somehow blocked the normal behaviour of usb_modeswitch (with the above config) and resulted in the modem switch happening only at startup (if I removed and reinserted the stick, nothing happened).

After I removed the file, everything worked normally. I could remove-reinsert the stick and the 3G connection always initialized properly.




Executing mode switch manually:
--------------------------------------
If, nothing helps, and the device doesn't get recognized automatically, when you plug it in, you can use this from the command line

```

sudo /usr/sbin/usb_modeswitch --default-vendor 0x12d1 --default-product 0x1446 --target-vendor 0x12d1 --target-product 0x1001 --message-content 55534243000000000000000000000011060000000000000000000000000000

```This is the same as in the udev rule file (from the RUN+=).

---

### Post by ssk_the_gr8 on 2011-04-19
i had the same issue with my huawei e1752
thanx a lot .. really helped me

---

### Post by sola on 2011-10-06
The above method works perfectly on a fresh install of Ubuntu 10.04 Lucid, I have just installed.

---

