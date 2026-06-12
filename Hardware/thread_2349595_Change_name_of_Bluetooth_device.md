---
title: "Change name of Bluetooth device"
date: 2017-01-16
forum: Hardware
---

### Post by adriaan4 on 2017-01-16
Hi all,

I found this to change the name of a Bluetooth Device in 16.04 LTS:

Go to 
/var/lib/bluetooth/computer_BT_id/connected_device_BT_id

Example:

[FONT=courier new]cd /var/lib/bluetooth/00:11:22:8A:5B:A3/B6:26:C9:9D:5C:16[/FONT]

edit the file info

Change the name.

Works for me, also after reboot.

---

