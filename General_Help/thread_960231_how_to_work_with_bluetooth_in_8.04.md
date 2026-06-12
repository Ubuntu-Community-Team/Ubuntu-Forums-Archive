---
title: "how to work with bluetooth in 8.04?"
date: 2008-10-27
forum: General Help
---

### Post by ittayd on 2008-10-27
Hi,

I have a pocket pc and I'm trying to connect to it from my laptop.

This is what I'm trying:
* connect to a device from the laptop: can't find how to do it. i can only connect from the device.
* see services my laptop offers (all are turned on in the bluetooth applet):  none is shown in the device (that is, i can connect to my laptop but do nothing with it).
* browse device from bluetooth applet: 'Error: Host down
Please select another viewer and try again.' (gnome-vfs-obexftp is installed and running gnome-obex-server)
*  sudo hidd --search: doesn't return anything 
* hcitool scan: shows my device (finally something!)
* but, sudo hidd --connect: gives me 'Can't get device information: Success'
* synce-pls: this is what I get:
** Message: Hal reports no devices connected

** (process:32654): WARNING **: No devices connected to odccm
synce-pls: Could not find configuration at path '(Default)'
* i tried 'sudo hciconfig hci0 reset', didn't help
* dmesg | grep Blue: gives nothing
* downgraded bluez-utils like some blogs suggested. no change.
* running synce-gnome didn't help either.

I'd appreciate any help, especially understanding what is going on (I feel like a monkey randomly punching commands in the terminal)

Thank you,
Ittay

---

