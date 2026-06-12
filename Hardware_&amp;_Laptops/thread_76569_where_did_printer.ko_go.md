---
title: "where did printer.ko go?"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by snowsquirrel on 2005-10-15
Recently I installed the display drivers from nVidia, and did a apt-get upgrade.  
Now I go to use my printer and realized that it is no longer recognized. lsmod does not show 'printer' which used to be the usb printer driver. (I just installed linux again after an abscense of about 3 years, so maybe things have changed. )

Searching through /lib/modules/$(uname -r) did not turn up a printer.ko?  Did it get removed somehow?

Do I have to do a kernel compile to get it to work?  I thought that with ubuntu those days were behind me?

Thanks,

~S

---

