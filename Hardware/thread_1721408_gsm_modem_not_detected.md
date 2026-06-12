---
title: "gsm modem not detected"
date: 2011-04-04
forum: Hardware
---

### Post by sudhir182 on 2011-04-04
I am using simcom gsm modem on ubuntu 10. I am able to make it work using minicom. But when I am using wvdial or gnome-ppp it says modem not detected.
Its not getting detected in rs232 and usb both cases. Please help me out.

---

### Post by wbloos on 2011-04-05
I had similar issues.
It turned out that the PIN would not work correctly. When i removed the PIN from the sim card (using windows, but a phone would've worked too), it worked.

HTH

---

### Post by sudhir182 on 2011-04-05
hi wbloos,
Thanks for reply....
But I check with command at+cpin? and it says READY .... so no further entry is required. Also I check using phone and PIN request is OFF.
But my modem is still not detected with wvdial/gnome-ppp.

---

