---
title: "Bluetooth failing after working for a while"
date: 2024-05-15
forum: Hardware
---

### Post by dgibbs7 on 2024-05-15
Folks:

I've got a problem with the bluetooth on my HP Elitebook 840 G10.

When I boot up the system, bluetooth works fine ... I'm just using it for my mouse at the moment.

After a while, I don't know how long, bluetooth stops working.  

I've combed through syslog to see if I can find anything that might indicate what is going wrong, and this is what I've found...

This is what is logged when I try to activate bluetooth ...

```
May 15 07:41:27 MYSYSTEM kernel: [85067.264144] Bluetooth: hci0: Opcode 0x0c03 failed: -110
May 15 07:41:29 MYSYSTEM kernel: [85069.280159] Bluetooth: hci0: Failed to read MSFT supported features (-110)
May 15 07:41:29 MYSYSTEM kernel: [85069.280626] Bluetooth: hci0: Hardware error 0x0c
May 15 07:41:29 MYSYSTEM bluetoothd[2649]: Failed to set mode: Authentication Failed (0x05)
May 15 07:41:39 MYSYSTEM kernel: [85079.520170] Bluetooth: hci0: Reset after hardware error failed (-110)
May 15 07:41:41 MYSYSTEM kernel: [85081.540149] Bluetooth: hci0: Opcode 0x0c03 failed: -110
May 15 07:41:41 MYSYSTEM kernel: [85081.540173] Bluetooth: hci0: MSFT extension not registered
```

I found this in syslog from late in the previous day...,.

```
May 14 20:36:24 MYSYSTEM kernel: [45164.455071] usb 3-10: reset full-speed USB device number 7 using xhci_hcd
May 14 20:36:24 MYSYSTEM kernel: [45164.590724] usb 3-10: device descriptor read/64, error -71
May 14 20:36:25 MYSYSTEM kernel: [45164.830684] usb 3-10: device descriptor read/64, error -71
May 14 20:36:25 MYSYSTEM kernel: [45165.066706] usb 3-10: reset full-speed USB device number 7 using xhci_hcd
May 14 20:36:25 MYSYSTEM kernel: [45165.198690] usb 3-10: device descriptor read/64, error -71
May 14 20:36:25 MYSYSTEM kernel: [45165.434734] usb 3-10: device descriptor read/64, error -71
May 14 20:36:25 MYSYSTEM kernel: [45165.670724] usb 3-10: reset full-speed USB device number 7 using xhci_hcd
May 14 20:36:25 MYSYSTEM kernel: [45165.670909] usb 3-10: Device not responding to setup address.
May 14 20:36:26 MYSYSTEM kernel: [45165.878829] usb 3-10: Device not responding to setup address.
May 14 20:36:26 MYSYSTEM kernel: [45166.090652] usb 3-10: device not accepting address 7, error -71
May 14 20:36:26 MYSYSTEM kernel: [45166.218660] usb 3-10: reset full-speed USB device number 7 using xhci_hcd

```

This is how lshw shows the bluetooth radio...


description: Bluetooth wireless interface
vendor: Intel Corp.
physical id: a
bus info: usb@3:a
version: 0.00
capabilities: bluetooth usb-2.01
configuration: driver=btusb maxpower=100mA speed=12Mbit/s



Other pertinent details about my system...

Linux MYSYSTEM 6.5.0-35-generic #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue May  7 09:00:52 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

Distributor ID: Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:        22.04
Codename:       jammy


Any suggestions where to look further?

Is this a hardware issue?

Thanks!

David

---

