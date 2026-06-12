---
title: "CX11N fails silently on 9.10"
date: 2009-11-03
forum: Hardware
---

### Post by jema on 2009-11-03
I have installed the drivers, but found pstoalcx11.sh came up as uninstalled until copied to /usr/bin

Having done this, there is evidently some connection to the printer on:

socket://192.168.0.190

as toner levels are reported correctly. Try and "Print test page" and no errors are reported, but no print occurs. Try "Print Self-Test Page" and a dialog: "CUPS server error There was an error during CUPS operaton: 'client-error-document-format-not-supported'" appears.

---

### Post by vinset on 2009-11-05
I have the same problem!

---

### Post by jema on 2009-11-05
I did a fresh 32bit install to see if that made any difference and this time did not install the CX11n drivers but left it on the CX21 driver that is there by default.
This driver also works to the extent that is sees the toner levels, but still fails silently on printing.
Not sure whether this driver really should work or not though.

---

### Post by jema on 2009-12-20
bump...

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=894493](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=894493)

Helps somewhat in establishing there is a missing library and you can get passed that error.

But for all that I'm still not getting the printer to work :(

this is becoming a real bind, I'm stuck on 8.10 because of this.

---

