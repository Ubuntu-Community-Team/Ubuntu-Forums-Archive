---
title: "USB audio interface not recognized"
date: 2017-11-18
forum: Hardware
---

### Post by SponezillA on 2017-11-18
Hello friends.I am trying to install my USB audio interface. The symptom I am experiencing is the exact same as documented here:[https://ubuntuforums.org/showthread.php?t=2279152&highlight=audiobox+usb](https://ubuntuforums.org/showthread.php?t=2279152&highlight=audiobox+usb) ```
 7062.581294] usb 1-3: new full-speed USB device number 18 using xhci_hcd[ 7063.947292] usb 1-3: device descriptor read/all, error -75[ 7064.065275] usb 1-3: new full-speed USB device number 19 using xhci_hcd[ 7064.207309] usb 1-3: device descriptor read/all, error -75[ 7064.325279] usb 1-3: new full-speed USB device number 20 using xhci_hcd[ 7064.349978] usb 1-3: unable to read config index 0 descriptor/all[ 7064.349985] usb 1-3: can't read configurations, error -75[ 7064.469263] usb 1-3: new full-speed USB device number 21 using xhci_hcd[ 7064.496930] usb 1-3: unable to read config index 0 descriptor/all[ 7064.496936] usb 1-3: can't read configurations, error -75[ 7064.496969] usb usb1-port3: unable to enumerate USB device 
```I too have an audiobox USB. This works perfectly in Windows 10. As the user in the example thread stated he found out that the usb cable is bad - I tried a different cable and experienced the same symptom.Could this be an incompatibility problem with my kernel? For the record I'm using Debian - but hey it's the same thing pretty much. ```
Linux j-St4tion 4.9.0-4-amd64 #1 SMP Debian 4.9.51-1 (2017-09-28) x86_64 GNU/Linux 
```

---

