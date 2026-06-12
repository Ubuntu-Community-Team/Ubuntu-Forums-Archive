---
title: "Webcam Stopped Working - Unable to Enumerate, Device not accepting address"
date: 2010-10-09
forum: Hardware
---

### Post by ravindasenarath on 2010-10-09
This problem was posted here and in other several posts also. But in any of those places there was not a solution.

I have my web cam working with Lucid Lynx fine till today. But suddenly it stops working. when I try dmesg it gives this.

```

[   25.864040] usb 2-1: new full speed USB device using uhci_hcd and address 6
[   25.984050] usb 2-1: device descriptor read/64, error -71
[   26.208040] usb 2-1: device descriptor read/64, error -71
[   26.424041] usb 2-1: new full speed USB device using uhci_hcd and address 7
[   26.544041] usb 2-1: device descriptor read/64, error -71
[   26.768039] usb 2-1: device descriptor read/64, error -71
[   26.984034] usb 2-1: new full speed USB device using uhci_hcd and address 8
[   27.392035] usb 2-1: device not accepting address 8, error -71
[   27.504032] usb 2-1: new full speed USB device using uhci_hcd and address 9
[   27.912067] usb 2-1: device not accepting address 9, error -71
[   27.912091] hub 2-0:1.0: unable to enumerate USB device on port 1


```

then I try all other ports but it did not help. 

[http://ubuntuforums.org/showthread.php?t=1572877](http://ubuntuforums.org/showthread.php?t=1572877)
this post tells the same problem. some one(dortmann) has tell that he solve it but for me it is not clear how. he says it is some thing with blacklisted modules.
and I saw number of bug reports of this. So any one know what is this. please update about it. 

Thank you

---

