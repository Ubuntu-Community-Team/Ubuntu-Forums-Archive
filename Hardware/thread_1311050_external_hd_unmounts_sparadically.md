---
title: "external hd unmounts sparadically"
date: 2009-11-02
forum: Hardware
---

### Post by afrodocter on 2009-11-02
i have a external maxtor usb hard drive, which used to work perfectly. i installed ubuntu 9.10, and now it sparadically unmounts. i have to unplug and re-plug the power to get it to re-mount.

dmesg yields this:
```

[57772.671013] EXT3-fs: mounted filesystem with writeback data mode.
[59447.161270] usb 1-4: reset high speed USB device using ehci_hcd and address 56
[59447.281270] usb 1-4: device descriptor read/64, error 18
[59447.511266] usb 1-4: device descriptor read/64, error 18
[59447.741274] usb 1-4: reset high speed USB device using ehci_hcd and address 56
[59447.861267] usb 1-4: device descriptor read/64, error 18
[59448.091273] usb 1-4: device descriptor read/64, error 18
[59448.321276] usb 1-4: reset high speed USB device using ehci_hcd and address 56
[59448.351670] usb 1-4: device descriptor read/8, error -61
[59448.481662] usb 1-4: device descriptor read/8, error -61
[59448.711522] usb 1-4: reset high speed USB device using ehci_hcd and address 56
[59448.741652] usb 1-4: device descriptor read/8, error -61
[59448.871642] usb 1-4: device descriptor read/8, error -61
[59448.990031] sd 16:0:0:0: Device offlined - not ready after error recovery
[59448.990036] usb 1-4: USB disconnect, address 56
[59449.120041] usb 1-4: new high speed USB device using ehci_hcd and address 57
[59449.232632] usb 1-4: device descriptor read/64, error 18
[59449.471267] usb 1-4: device descriptor read/64, error 18
[59449.701278] usb 1-4: new high speed USB device using ehci_hcd and address 58
[59449.844157] usb 1-4: device descriptor read/64, error 18
[59450.080267] usb 1-4: device descriptor read/64, error 18
[59450.302091] usb 1-4: new high speed USB device using ehci_hcd and address 59
[59450.332931] usb 1-4: device descriptor read/8, error -61
[59450.470687] usb 1-4: device descriptor read/8, error -61
[59450.691552] usb 1-4: new high speed USB device using ehci_hcd and address 60
[59450.722910] usb 1-4: device descriptor read/8, error -61
[59450.851903] usb 1-4: device descriptor read/8, error -61
[59450.961538] hub 1-0:1.0: unable to enumerate USB device on port 4
[59451.281519] usb 4-2: new full speed USB device using uhci_hcd and address 57
[59451.412508] usb 4-2: device descriptor read/64, error 18
[59451.651493] usb 4-2: device descriptor read/64, error 18
[59451.882480] usb 4-2: new full speed USB device using uhci_hcd and address 58
[59452.011272] usb 4-2: device descriptor read/64, error 18
[59452.251294] usb 4-2: device descriptor read/64, error 18
[59452.481267] usb 4-2: new full speed USB device using uhci_hcd and address 59
[59452.519455] usb 4-2: device descriptor read/8, error -61
[59452.652446] usb 4-2: device descriptor read/8, error -61
[59452.881427] usb 4-2: new full speed USB device using uhci_hcd and address 60
[59452.921628] usb 4-2: device descriptor read/8, error -61
[59453.063424] usb 4-2: device descriptor read/8, error -61
[59453.171271] hub 4-0:1.0: unable to enumerate USB device on port 2

```


the "offlined" error seems to be it, but im not sure how to fix this. 

thanks for the help
alex

---

### Post by afrodocter on 2009-11-06
i have also tried manual mounting, and the same behavior occurs. i noticed this exactly when i changed to 9.10 (maybe a different hd controller driver?). the drive is a Maxtor OneTouch 750 GB.

also the new "disk utility" reports '197-current pending sector count'. im not sure if this is related. i have already fsck'd the drive, and fixed any fs errors.

thanks
alex

---

### Post by afrodocter on 2009-11-14
update:
i took out the drive and just use it as an internal. works fine, so it must have been the enclosure driver. 
once again it was a 

Maxtor OneTouch 4 Plus 750G on  2.6.31-14-generic

---

