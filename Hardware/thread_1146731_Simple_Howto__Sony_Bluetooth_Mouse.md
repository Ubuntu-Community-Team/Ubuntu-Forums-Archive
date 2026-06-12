---
title: "Simple Howto:  Sony Bluetooth Mouse"
date: 2009-05-02
forum: Hardware
---

### Post by em3raldxiii on 2009-05-02
Okay, quick background on my setup:

Ubuntu 8.04
MSI GT735 Laptop with built-in Bluetooth.
Sony Wireless Mouse that shows up as VGP-VMS33 in the gnome bluetooth app.

Problem:  Will not connect with the bluetooth tool, gives me an error.

Solution:  As per one of the bluetooth howtos, type this in a console to make the mouse work for this session:

```
sudo hidd --search
```

That's it.  As soon as I typed that in, the mouse worked.

Cheers!

---

