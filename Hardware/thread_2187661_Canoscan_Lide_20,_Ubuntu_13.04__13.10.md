---
title: "Canoscan Lide 20, Ubuntu 13.04 / 13.10"
date: 2013-11-13
forum: Hardware
---

### Post by haedri on 2013-11-13
Hi,

My Canoscan Lide 20 scanner does not work on Ubuntu 13.04, but it works just fine on Ubuntu 12.04, I tried :
[LIST]
[*]xsane : it will search a scanner, then the window disappear and no new window appears, but the program is still running in the background, probably in a blocked state, no message in console 
[*]simple scan : when clicking the scan button the "loading" animation appears, nothing more, it stays in loading mode forever, the scanner doesn't make any sound (no calibration whatsoever) 
[*]using different ports / cables : same result 
[*]using simple scan on Ubuntu 12.04 : it works fine 
[/LIST]

Nothing special in dmesg:
```
[  648.460270] usb 3-2: new full-speed USB device number 10 using xhci_hcd
[  648.477521] usb 3-2: New USB device found, idVendor=04a9, idProduct=220d
[  648.477528] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  648.477532] usb 3-2: Product: CanoScan
[  648.477535] usb 3-2: Manufacturer: Canon
```

I finally tried [VueScan]("http://www.hamrick.com/"), the scanner seems to work fine with it, but it's not a free software, and there's a watermark applied to the scanned image. But if I
[LIST=1]
[*]Launch VueScan 
[*]Scan an image 
[*]Cancel scan and exit VueScan 
[*]Launch Simple Scan 
[*]Scan an image 
[/LIST]
Then Simple Scan will work perfectly well until I unplug my scanner, if I plug the scanner again, same problem

So it's not a computer/usb problem nor a scanner problem, the only problem seems to have to do with Ubuntu 13.04

My guess is that there's a problem initializing the scanner since Ubuntu 13.04, VueScan somehow make the initialization correctly, which allow other programs to work afterwards, but it's not a very good solution.

Any idea what I could do to make it work without using a proprietary/closed source program ?

---

### Post by mossfoot2 on 2014-02-06
I hope something comes of this, because I'm encountering the same problem with the same device (but can't seem to use your trick/workaround)

---

### Post by haedri on 2014-02-06
I just did a quick test, it seems to work better now that I've upgraded to ubuntu 13.10
Sometimes Simple Scan tells me there was an error, sometimes it works (just by restarting it), it's quite random, but I'm able to scan pages

---

### Post by Radi Filali on 2014-02-18
It works after reset:
usb_modeswitch -v 0x04a9 -p 0x220d -R

---

