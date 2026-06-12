---
title: "Sony Ericsson G502 not detected on Gammu"
date: 2012-05-30
forum: Hardware
---

### Post by alfian on 2012-05-30
hi there, i wanna ask why does my phoe SE G502 not detected in gammu?
here my dmesg tail output
```
[ 1550.973816] usb 3-2: USB disconnect, device number 6
[ 1550.978158] ohci_hcd 0000:00:03.1: dma_pool_free buffer-128, edc1a000/2dc1a000 (bad dma)
[ 1550.979145] cdc_ether 3-2:3.8: usb0: unregister 'cdc_ether' usb-0000:00:03.1-2, CDC Ethernet Device
[ 1732.164087] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 1732.816075] usb 3-2: new full-speed USB device number 7 using ohci_hcd
[ 1733.072203] cdc_acm 3-2:3.1: ttyACM0: USB ACM device
[ 1733.084197] cdc_acm 3-2:3.3: ttyACM1: USB ACM device
[ 1733.102298] cdc_wdm 3-2:3.7: cdc-wdm0: USB WDM device
[ 1733.113407] cdc_ether 3-2:3.8: usb0: register 'cdc_ether' at usb-0000:00:03.1-2, CDC Ethernet Device, 02:80:37:ff:02:00

```

i had configured .gammurc file to
```

device = /dev/ttyACM0
connection = at

```

but when the output command from 
```
gammu --identify
```

is

```
Error during reading rom the device
```

any suggestion?
(i'm using ubuntu 10.10 with gammu 1.27)

---

