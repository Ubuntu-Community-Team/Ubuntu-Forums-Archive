---
title: "Problems scanning in Maverick"
date: 2010-11-07
forum: Hardware
---

### Post by chylee on 2010-11-07
I having problems scanning using my Epsom Perfection 1650. I using gscan2pdf which finds the scanner but when I attempt to scan I get the following error "Operation was Cancelled". After the error I have to reconnect the usb on the scanner for gscan2pdf to see the scanner. When using xsane I got the same problems. I ran xsane from the command line and tried scanning and got this message "[epson2] e2_ext_read: cancel request received" then I tried scanimage -L which can’t find the scanner. This was working fine in kubuntu 10.04

---

### Post by uhappo on 2010-11-08
I get the same
```
Operation was Cancelled
```
error when using xsane, preview works but the actual scan ends up with that error.

Simple scan (I'm using Ubuntu 10.10 64bit) works ok, I can live with that for a moment but I'd rather use xsane.

---

### Post by chylee on 2010-11-10
This worked for me. Edit file '/etc/sane.d/dll.conf' comment out 'epson2' and
uncomment 'epson'

goto [http://kubuntuforums.net/forums/index.php?topic=3114501.0]("http://kubuntuforums.net/forums/index.php?topic=3114501.0") for more info

---

### Post by uhappo on 2010-11-10
Ah, my bad, my reply was a bit short on info...

I'm using Canon Pixma mp160, so I'm out of luck this time...

---

### Post by chylee on 2010-11-10
It seem to be a bug report uhappo. Look at '[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=585887]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=585887")' this person seem to have the same problem. No solution.

---

### Post by uhappo on 2010-11-12
Yeah, a bug.

This needs to be sorted out!

---

### Post by uhappo on 2010-12-01
Some progress, I think?
[http://lists.alioth.debian.org/pipermail/sane-devel/2010-November/027736.html]("http://lists.alioth.debian.org/pipermail/sane-devel/2010-November/027736.html")

---

