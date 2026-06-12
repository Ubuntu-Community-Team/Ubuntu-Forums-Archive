---
title: "SMART Data &amp; Self-Tests on external USB 3.0 HDD"
date: 2015-05-27
forum: Hardware
---

### Post by pieter512 on 2015-05-27
Hello

I would like to check an external USB 3.0 HDD ([this one]("http://www.wdc.com/en/products/products.aspx?id=470")) for bad sectors. 
I tried the preinstalled 'Disks' utility, but the 'SMART Data & Self-Tests' option is greyed out for every USB HDD connected. It does work for my 3 internal drives however ... So I tried opening the case of the harddisk, to see if I could connect it with a regular sata cable, but these newer models seem to have the usb-interface built in (instead of a sata-usb converter) so this is not an option. 
Is there a package/utility I could try, or do usb harddrives simply not support SMART?

Thanks in advance
Pieter

---

### Post by weatherman2 on 2015-05-27
Install GSmartControl, which has a better S.M.A.R.T. interface.

GSmartControl is a graphic interface to smartctl, a terminal command for running S.M.A.R.T. and checking Attributes and status.  You can query a drive's current status with this command:

```
sudo smartctl -a /dev/sda
```

(for drive /dev/sda ).

Many USB controllers are not automatically found, but you can add options to smartctl to try to pick them up.  I have been able to access S.M.A.R.T. on pretty much all of my USB drives this way:

```

smartctl -a -T permissive /dev/sda
smartctl -a -d sat /dev/sda
smartctl -a -T permissive -d sat /dev/sda

```

Other -d options are given here for different controllers:

[https://www.smartmontools.org/wiki/Supported_USB-Devices](https://www.smartmontools.org/wiki/Supported_USB-Devices)

---

### Post by pieter512 on 2015-05-28
The GSmartControl utility works just fine.
Thanks a lot!

---

