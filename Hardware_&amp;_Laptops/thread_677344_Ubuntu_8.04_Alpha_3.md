---
title: "Ubuntu 8.04 Alpha 3"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by SpyroViper on 2008-01-24
Hi,

I'm having problems setting up my Toshiba P100 Satellite Laptop with 8.04.

I know its still in development, but I cannot get my Geforce Go 7600 to work at my native resolution.
Restricted Drivers says its in use (the driver) and I have re-installed the glx-new from Symantic.  I have no idea what is going on, any help will be greatly appreciated.

Thanks in advance.




:guitar:

---

### Post by Mze on 2008-01-24
Run this command in the terminal window:

sudo dpkg-reconfigure -phigh xserver-xorg

See if you can select a higher resolution from the list and reboot your machine.

---

### Post by SpyroViper on 2008-01-25
Thanks, it worked but then re-did what I explained above.  I updated though (tonights update) and I have video, resolution ANNND! My HD audio sound is fixed.

Thank you for helping
:popcorn:

---

