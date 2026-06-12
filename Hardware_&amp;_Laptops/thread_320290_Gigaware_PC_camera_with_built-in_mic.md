---
title: "Gigaware PC camera with built-in mic"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by ShadowRage on 2006-12-17
Well, this seems to be a completely new chipset as linux only sees it as a partially working USB microphone, either the webcam is defective (gonna test with vmplayer and XP..) or I have something unknown. I like this little webcam because it's LCD monitor friendly (as in, it can hang on my LCD monitor) and I dont want to have to take it back and go back to using my ancient "webcam" :(

anyway, the relative dmesg output: 

[403435.835631] usb 1-1: new full speed USB device using ohci_hcd and address 11
[403436.232987] usbcore: registered new driver snd-usb-audio

that's it. doesnt create a new video device or anything.

relative lsusb output:

Bus 001 Device 011: ID 093a:260e Pixart Imaging, Inc.

nothing supports it. the spca5xx driver doesnt, the gspca driver (newer version) doesnt support it... So, what can I do?

edit: XP doesnt seem to like it either, may be defective..

---

### Post by jazzroy on 2007-01-28
hi, 
same problem here.
but in XP it work perfectly :(

---

### Post by ossguy on 2007-02-17
There's some work being done to build a driver for this camera by Thomas Kaiser.  You can see what he's done so far at his PAC7311 page ([http://www.kaiser-linux.li/index.php?title=PAC7311]("http://www.kaiser-linux.li/index.php?title=PAC7311")).  It doesn't look like there's a driver ready to go at this point, but hopefully there will be one in the not too distant future.

---

### Post by ossguy on 2007-05-21
Support for this web cam has been added in version 1.00.18 of the gspcav1 driver ([http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)).  Thomas' page has some additional instructions for Feisty users ([http://www.kaiser-linux.li/index.php?title=PAC7311](http://www.kaiser-linux.li/index.php?title=PAC7311)).  The picture quality still needs some work, but it's a good start for those wanting functionality for their PAC7311 web cams.

---

