---
title: "Samsung SGH-U800 via USB"
date: 2011-04-07
forum: Hardware
---

### Post by weekend_player on 2011-04-07
I want to connect my Samsung SGH-U800 mobile phone to ubuntu and share files via USB cable. The MTP mode worked for some time but recently it stopped. The mass storage mode causes the cellphone to restart.

After some time being connected this error message appears:
```
Can't open device Samsung YH-999 Portable Media Center/SGH-A707/SGH-L760V/SGH-U900/Verizon Intensity
```

I used gphotofs as suggested here: ```
http://translate.google.com/translate?js=n&prev=_t&hl=pl&ie=UTF-8&layout=2&eotf=1&sl=pl&tl=en&u=http%3A%2F%2Flinux360.pl%2Fforum%2Fthread-2310.html
```

```
dmesg
[ 5279.084038] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 5286.838956] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 5287.002599] usb 4-1: configuration #1 chosen from 1 choice
[ 5318.688523] usb 4-1: reset full speed USB device using uhci_hcd and address 6
(and so on...)
[ 5572.480548] usb 4-1: USB disconnect, address 6
```

```
lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 04e8:5a0f Samsung Electronics Co., Ltd MTP Device
Bus 004 Device 002: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 06b9:4061 Alcatel Telecom SpeedTouch ISDN or ADSL Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
uname -srvo
Linux 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 GNU/Linux
```

Best regards

---

### Post by afrodeity on 2011-12-03
No luck with Samsung E2220, unable to enumerate device

---

### Post by difiCa on 2011-12-03
I'm not an expert on Samsung phones, but at least my Nokia N8 works fine with Ubuntu in mass storage mode and I don't see a reason why your phone wouldn't. What I'd do is either update or reinstall the firmware on your phone if you have some means of doing so and try again, the phone booting after connecting the USB sounds like a bug or a fault in your phone firmware.

---

