---
title: "&quot;Safely Remove&quot; disconnects built-in USB card reader"
date: 2011-05-13
forum: Hardware
---

### Post by BlackDex on 2011-05-13
Hello there,

I Have a laptop with a built-in card reader.
If i put a SD-Card in, and then "Safely Remove" it when im done.
It compleetly removes the whole USB device, instead of just un-mounting the card.

Now i have to reboot to get this device working again.
How can i prevent this device from being unplugged/disconnected and still be able to have the device unmount/removed correctly??

Or, how can i re-detect the USB devices, so i don't have to reboot?

Thx in advance.

---

### Post by fstrube on 2011-06-23
I ran into this problem and the following steps worked for me.
[LIST=1]
[*]Unmount all USB/Mass Storage devices and make sure none are in use
[*]Run the following code in the terminal: ```
sudo modprobe -r usb_storage && sleep 2 && sudo modprobe usb_storage
```
[/LIST]

---

