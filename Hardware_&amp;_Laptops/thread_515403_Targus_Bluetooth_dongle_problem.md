---
title: "Targus Bluetooth dongle problem"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by byronpdx on 2007-08-01
I have a Targus ACB10US Bluetooth dongle. It is recognized by the system, and using Gnome the Bluetooth applet comes up and says that it is now connected. However, when I run hcid - n I get the following:
```
:~$ sudo hcid -n
hcid[3456]: Bluetooth HCI daemon
hcid[3456]: HCI dev 0 registered
hcid[3456]: HCI dev 0 already up
hcid[3456]: Device hci0 has been added
hcid[3456]: Starting security manager 0
hcid[3456]: Can't write inquiry mode for hci0: Input/output error (5)
hcid[3456]: Getting name failed with status 0x0c
hcid[3456]: Getting scan enable failed with status 0x0c
hcid[3456]: Default passkey agent (:1.12, /org/bluez/applet) registered
```
When I try and connect a bluetooth headset or a phone it does not respond. I run hcitool scan and I get errors similar to the above saying that it fails. 

Is this a known problem? Is there a fix? Is this dongle just not compatible with Linux?

Thanks.

---

