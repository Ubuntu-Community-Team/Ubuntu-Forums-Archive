---
title: "Webcam install Trust Wb1200"
date: 2008-08-01
forum: Hardware
---

### Post by micdhack on 2008-08-01
Im having a trust webcam and i cant get it to work. I visited this page:
[https://help.ubuntu.com/community/Spca5xx#Ubuntu%207.10%20(Gutsy),%20and%208.04%20(Hardy](https://help.ubuntu.com/community/Spca5xx#Ubuntu%207.10%20(Gutsy),%20and%208.04%20(Hardy))
which say that i need to enable only the moded which i did and i have result for lsmod
```
gspca                 680528  0 
videodev               29440  1 gspca
usbcore               146028  9 gspca,usb_storage,libusual,usbhid,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd
```

I have also camorama installed and when i am trying to run it /dev/video0 says it doesnt exists. This is not because i dont have root access on the file but because when i do an ls /dev/ |grep video the file doesnt exist.

Any ideas?

During connection and disconnection of the usb camere i get this from dmesg
```
[18768.021837] usb 3-5: USB disconnect, address 11
[18772.979763] usb 3-5: new high speed USB device using ehci_hcd and address 12
[18773.114580] usb 3-5: configuration #1 chosen from 1 choice

```

---

### Post by micdhack on 2008-08-01
turn out you need a specific driver for its model of microdia but its easy to find because they have a google group here:

[http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/)

They have step by step guide to help you with the installation also.

---

