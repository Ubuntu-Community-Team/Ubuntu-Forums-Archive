---
title: "Problem with PixArt 093a:2600"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by Rieg on 2007-11-25
Hello everybody!

I can't get my WebCam to work. 
I have read all related topics in this forum, but nothing really helps.

Here are the steps i performed until now:

Downloaded the correct drivers from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
untared the tar - File.
executed the following commands in the new directory:
make
sudo make install

lsusb shows the following line:
```
Bus 002 Device 005: ID 093a:2600 Pixart Imaging, Inc.
```

and dmesg shows only these lines:
```
[  139.460000] usb 2-2: new full speed USB device using uhci_hcd and address 5
[  139.680000] usb 2-2: configuration #1 chosen from 1 choice

```

Several programs like Ekiga or Camorama tell me that no video device is found :(

---

### Post by spegru on 2007-11-26
I have the same problem with Emprex PC-380S
From the error message, no suitable driver was found

This strange however because according to mxhaard in this thread 

[http://osdir.com/ml/drivers.spca50x.devel/2005-09/msg00049.html](http://osdir.com/ml/drivers.spca50x.devel/2005-09/msg00049.html)

it was supported from 2005.....

Maybe there is another problem.....

spegru

---

