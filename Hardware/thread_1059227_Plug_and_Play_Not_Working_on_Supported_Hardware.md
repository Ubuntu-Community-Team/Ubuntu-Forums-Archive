---
title: "Plug and Play Not Working on Supported Hardware"
date: 2009-02-03
forum: Hardware
---

### Post by TSS on 2009-02-03
I've got a USB mouse and a flash drive that both work with Ubuntu.  On previous versions (8.04 I believe), they would be detected just fine when I plugged them in.  On 8.10 however, plug and play doesn't seem to work (nothing shows up in the output of 'lsusb').  If I plug in the hardware before Ubuntu starts up, everything is fine.  Any ideas on how I can more accurately diagnose why plug and play is not working?

---

### Post by ajmorris on 2009-02-04
> **TSS said:**
> I've got a USB mouse and a flash drive that both work with Ubuntu.  On previous versions (8.04 I believe), they would be detected just fine when I plugged them in.  On 8.10 however, plug and play doesn't seem to work (nothing shows up in the output of 'lsusb').  If I plug in the hardware before Ubuntu starts up, everything is fine.  Any ideas on how I can more accurately diagnose why plug and play is not working?

hi there,
after plugging in the USB devices in question. You can run:
```
sudo dmesg
``` A message about the USB devices, should be appended to that output when they are plugged in. If you would like help in debugging the issue, please paste here, the output of that command.

AJ

---

### Post by TSS on 2009-02-05
Here's the output of 'lsusb' when the USB mouse is plugged in before boot:
```

**Bus 001 Device 003: ID 046d:c51b Logitech, Inc.** 
Bus 001 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 002 Device 006: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 005: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Here's the output of 'sudo dmesg' when I plug it in after boot:
```

[15057.755837] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f53a13c0
[15058.778829] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f53a13c0
[15059.701161] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f53a13c0
[15060.724498] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f53a13c0
[15061.748575] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f53a13c0
[15062.772637] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f53a13c0
[15063.796713] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f53a13c0
[21019.447390] usb 1-8: USB disconnect, address 3

```

The USB disconnect must be from me unplugging the mouse before plugging it back in again.  Since there are no entries after that, am I correct in saying that there's absolutely no recognition or response from the USB port?

---

### Post by TSS on 2009-02-05
Hrm.  I was messing around with mounting and umounting volumes through nautilus, and I got a notification saying that I didn't have the permisions to do it.  I authorized myself and told nautilus to remember the authorization.  Apparently that fixed my problem.  It's pretty much a fresh install of 8.10, so I have no idea why the permissions would have been set up like that.  I wish I could be more precise, but I guess that's the end of it :-).

EDIT: Apparently marking a thread solved is no longer under thread tools?  I edited the title as a replacement.

---

