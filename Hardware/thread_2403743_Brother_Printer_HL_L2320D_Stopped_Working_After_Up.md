---
title: "Brother Printer HL L2320D Stopped Working After Upgrade"
date: 2018-10-15
forum: Hardware
---

### Post by braznyc on 2018-10-15
I've been using this Brother printer since Ubuntu 14.04.
Today when I upgraded Ubuntu to 18.04 the printer stopped working.

Any help is welcome. I need this printer for business.

---

### Post by pqwoerituytrueiwoq on 2018-10-15
did you try re-installing the driver for it
My networked 2360dw was auto detected after a clean install and works without the office drivers, i think it is slower to print and lacks the toner saver feature when compared to the official driver, but it does work out of the box

---

### Post by braznyc on 2018-10-15
I tried to reinstall the driver and it didn't work.

---

### Post by braznyc on 2018-10-17
These 2 commands made the printer work again:

sudo rmdir /usr/share/ghostscript/9.25/iccprofiles
sudo apt-get install --reinstall libgs9-common

---

### Post by noleks on 2018-10-18
I came to this forum with the same problem on my MFC-9130CW.  It took me one minute to paste those two commands into my terminal and test the fix.
Ubuntuforums forever!!!

---

### Post by braznyc on 2018-10-18
> **noleks said:**
> I came to this forum with the same problem on my MFC-9130CW.  It took me one minute to paste those two commands into my terminal and test the fix.
Ubuntuforums forever!!!


Nice! I'm glad it worked for you too!

---

### Post by gordon33 on 2018-10-18
Thank you it also worked for me.

---

