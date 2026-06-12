---
title: "Long boot delay (190 secs total) Bootchart attached"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Beastie Boy on 2009-04-25
I have just done a fresh install of 9.04 on my Acer Aspire 9110 series laptop. The boot process pauses at around 11 seconds, and this seems to be the point at which the Bluetooth device is switched on. The Bluetooth is controlled by a button along with the wireless network device. I usually leave Bluetooth off, but 9.04 insist on switching it on for some reason.
I never had this problem with previous versions.

Here is the dmesg output from the period when the delay occurs:

[   11.110893] EIP: [<f7fa52c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ES
P 0068:f619bc54
[   11.110906] ---[ end trace 9bd66193deb28a9c ]---
[   11.500080] Clocksource tsc unstable (delta = -341257333 ns)
[   11.588074] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   11.759586] usb 4-2: configuration #1 chosen from 1 choice
[   11.790916] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   11.791032] usbcore: registered new interface driver btusb
[  189.996709] lp: driver loaded but no devices found
[  190.062114] Adding 506008k swap on /dev/sda5.  Priority:-1 extents:1 across:5
06008k


Any help would be appreciated as one of my main reasons for upgrading to 9.04 was quicker boot.
I don't use Bluetooth and would be happy if the device wasn't loaded. I have looked to see if it can be disabled in the BIOS, but there is no option for it.

Many thanks, Beastie.

---

### Post by dtoronto on 2009-04-25
Can you enable boot logging?

```
$ sudo vi /etc/default/bootlogd
```

change the following line:

```
BOOTLOGD_ENABLE=No
```

to

```
BOOTLOGD_ENABLE=Yes
```

check your /var/log/boot after booting to see what's going on. You may want to post the output of your log on this forum to give a better idea of what is not loading correctly and why.

---

### Post by Beastie Boy on 2009-04-25
Thanks for your reply. I set BOOTLOGD_ENABLE=Yes, but after a reboot, the log still says (Nothing has been logged yet.) Not sure what is wrong there.

Is there any way to prevent the btusb driver from loading, and therefore stop it searching for devices. This search is what seems to be taking all the time.

Cheers, Beastie.

---

### Post by Beastie Boy on 2009-04-25
Is it possible to prevent the boot process from automatically switching on the usb BlueTooth device?
If not, can the length of time spent searching for devices be reduced? 3 minutes is crazy long. If I could adjust it to 1 second or less that would be great.

Cheers, Beastie.

---

