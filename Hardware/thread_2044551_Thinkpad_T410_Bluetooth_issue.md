---
title: "Thinkpad T410 Bluetooth issue"
date: 2012-08-19
forum: Hardware
---

### Post by atyauristen on 2012-08-19
Hello,

I connect my Thinkpad to a bluetooth speaker and the issue is that the sound is as if some packets were lost during the 2m trip they have to make. Similar when you watch a stream and the quality is not the best, the sound is not smooth.

With Windows 7 it's flawless, also I tried with two different phones.

I guess it has to be the bluetooth driver.

I'm using the latest Ubuntu 12.04 with 3.2.0-29-generic-pae.


> bla@bla:~$ modinfo bluetooth
filename:       /lib/modules/3.2.0-29-generic-pae/kernel/net/bluetooth/bluetooth.ko
alias:          net-pf-31
license:        GPL
version:        2.16
description:    Bluetooth Core ver 2.16
author:         Marcel Holtmann <marcel@holtmann.org>
srcversion:     62F1BC97A52542226443E43
depends:        
intree:         Y
vermagic:       3.2.0-29-generic-pae SMP mod_unload modversions 686 
parm:           disable_esco:Disable eSCO connection creation (bool)
parm:           disable_ertm:Disable enhanced retransmission mode (bool)
parm:           enable_mgmt:Enable Management interface (bool)
parm:           enable_le:Enable LE support (bool)


Do you have any idea what could cause this effect?

Thanks for the help!

Balázs

---

