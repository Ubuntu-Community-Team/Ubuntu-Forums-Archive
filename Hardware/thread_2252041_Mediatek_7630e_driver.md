---
title: "Mediatek 7630e driver"
date: 2014-11-08
forum: Hardware
---

### Post by alex289 on 2014-11-08
Hi guys!

I have trouble getting my MEDIATEK Corp. MT7630e adapter to work on 3.13 kernel.

I've downloaded drivers from their website and for a while I've been using their sh script to load drivers after each system boot up for quite some time(maybe 2months) . 
But for some reason I can not do it any longer I'm getting an error:

> ./rt2800pci.ko: Unknown symbol in module


The script they provided is load.sh :
```

insmod /lib/modules/$(uname -r)/kernel/drivers/misc/eeprom/eeprom.koinsmod /lib/modules/$(uname -r)/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
insmod /lib/modules/$(uname -r)/kernel/lib/crc-ccitt.ko
insmod /lib/modules/$(uname -r)/kernel/net/wireless/cfg80211.ko
insmod /lib/modules/$(uname -r)/kernel/net/mac80211/mac80211.ko
insmod ./rt2x00lib.ko;
insmod ./rt2x00pci.ko;
insmod ./rt2800pci.ko;
insmod ./rt2x00mmio.ko;
insmod ./rt2800lib.ko;



```

The whole output i get when I run sudo bash load.sh :
```
insmod: ERROR: could not load module /lib/modules/3.13.0-24-generic/kernel/drivers/misc/eeprom/eeprom.ko: No such file or directoryinsmod: ERROR: could not load module /lib/modules/3.13.0-24-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko: No such file or directory
insmod: ERROR: could not insert module /lib/modules/3.13.0-24-generic/kernel/lib/crc-ccitt.ko: File exists
insmod: ERROR: could not insert module /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko: File exists
insmod: ERROR: could not insert module /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko: File exists
insmod: ERROR: could not insert module ./rt2x00lib.ko: File exists
insmod: ERROR: could not insert module ./rt2x00pci.ko: File exists
insmod: ERROR: could not insert module ./rt2800pci.ko: Unknown symbol in module
insmod: ERROR: could not insert module ./rt2x00mmio.ko: File exists
insmod: ERROR: could not insert module ./rt2800lib.ko: File exists



```

What could be the problem?
 I've tried some other ways of loading drivers that are described [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125") and [here]("http://community.linuxmint.com/tutorial/view/1796") but it didn't help and the error for that particular file occurs anyways.

I'm on 3.13.0-24-generic kernel

Does anyone have any suggestions how to fix this?

---

### Post by alex289 on 2014-11-08
Also dmesg gives this:
> [   46.584925] input: Logitech Gaming Mouse G400 as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/input/input23[   46.586139] hid-generic 0003:046D:C245.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech Gaming Mouse G400] on usb-0000:00:14.0-1/input0
[   46.586675] hid-generic 0003:046D:C245.0003: hiddev0,hidraw2: USB HID v1.10 Device [Logitech Gaming Mouse G400] on usb-0000:00:14.0-1/input1
[   80.214475] rt2800pci: Unknown symbol eeprom_93cx6_multiread (err 0)
[   90.815473] rt2800pci: Unknown symbol eeprom_93cx6_multiread (err 0)




---

### Post by alex289 on 2014-11-10
Welp, had to swap my wifi adapter for atheros. Work perfectly now. Unfortunate that there are still problems with wifi in linux.

---

