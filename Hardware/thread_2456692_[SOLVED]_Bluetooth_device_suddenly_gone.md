---
title: "[SOLVED] Bluetooth device suddenly gone"
date: 2021-01-17
forum: Hardware
---

### Post by rinzewind on 2021-01-17
Hi everybody,

I have a Dell Vostro 15 3000 running (X)Ubuntu 18.04. It's been working well, but yesterday I noticed the Blueetoch icon missing from the taskbar and started investigating why.

The issue seems to be that the Bluetooth device my computer has is gone. This is a normal startup log, or at least what I understand to be normal, from kern.log:

```
Jan  4 08:24:15 serenity kernel: [   10.593120] Bluetooth: Core ver 2.22
Jan  4 08:24:15 serenity kernel: [   10.593130] NET: Registered protocol family 31
Jan  4 08:24:15 serenity kernel: [   10.593131] Bluetooth: HCI device and connection manager initialized
Jan  4 08:24:15 serenity kernel: [   10.593134] Bluetooth: HCI socket layer initialized
Jan  4 08:24:15 serenity kernel: [   10.593135] Bluetooth: L2CAP socket layer initialized
Jan  4 08:24:15 serenity kernel: [   10.593136] Bluetooth: SCO socket layer initialized
```

However, yesterday this appeared in the logs upon startup:

```
Jan 16 09:31:51 serenity kernel: [   19.944964] Bluetooth: hci0: command 0x0c52 tx timeout
```

After this happened, no more Bluetooth. I tried restarting, I tried an older kernel, I double-checked the Bluetooth is activated in the BIOS, I tried loading manually the necessary kernel modules. I've listed those using a similar laptop I have, and are the following:

```
bluetooth             544768  14 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  1 bluetooth
```

However, it's like the device is not there.

Also, this started showing up in kern.log now:

```
Jan 16 20:13:34 serenity kernel: [    2.768790] usb 1-10: device descriptor read/64, error -71
Jan 16 20:13:34 serenity kernel: [    3.004853] usb 1-10: device descriptor read/64, error -71
```

I'm absolutely puzzled. The problem looks very similar to the one posted [here]("https://bbs.archlinux.org/viewtopic.php?id=193813"), but I've tried resetting the device and it doesn't work. The laptop has been off all night and the device is still missing. If anyone could point me in the right direction I'd be grateful.

Thanks a lot in advance

---

### Post by rinzewind on 2021-01-24
Ok, I managed to solve this issue. It was a purely hardware issue. After finding [this discussion in the Dell support forums]("https://www.dell.com/community/Inspiron/Bluetooth-gone-G3/td-p/7405868"), I tried turning the laptop off **and** unplugging the battery. The next time the system went up, the Bluetooth device was there, and that mysterious USB device was gone.

---

