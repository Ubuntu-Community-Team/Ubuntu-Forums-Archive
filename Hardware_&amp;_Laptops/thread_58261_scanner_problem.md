---
title: "scanner problem"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by dskloet on 2005-08-19
Hi,

I try to get my scanner working...
I got the firmware file (Gt680xfw.usb) from the vendor cd and put it in /usr/share/sane/gt68xx.
Then I edited /etc/sane.d/snapscan.conf and changed the "firmware /path..." line to "firmware /usr/share/sane/gt68xx/Gt680xfw.usb".

Now when I try to use sane it says "[gt68xx] Couldn't open firmware file (neither `/usr/share/sane/gt68xx/PS1fw.usb' nor `/usr/share/sane/gt68xx/ps1fw.usb'): No such file or directory". It is correct in saying that but why is it looking for the wrong firmware file? (PS1fw.usb instead of Gt680xfw.usb)

My scanner is a Lifetec LT 9385.
Any help would be highly appreciated,

David

---

### Post by humanity_to_others on 2005-08-20
I think you should edit /etc/sane.d/gt68xx.conf too
```
sudo gedit /etc/sane.d/gt68xx.conf
``` and remove # from your scanner device name

---

### Post by dskloet on 2005-08-21
That worked.
Thanks a lot.

---

