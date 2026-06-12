---
title: "How does Ubuntu make a bcm43xx wireless chip work?"
date: 2009-05-31
forum: Hardware
---

### Post by Kingoftherings on 2009-05-31
I bought a laptop, and I was dismayed to find it had a Broadcom wifi chip. (I didn't do very good research apparently)  But I was overjoyed to find that Ubuntu made it work.

How does the Broadcom driver in the Restricted Hardware section work?  Does it just use ndiswrapper, or is there some other method now?

I'd like to find out so I can apply that method to other distros.

---

### Post by lswest on 2009-05-31
There are 3 drivers:

- bcm43xx - this one is basically a firmware hack that rips the firmware from a .exe and puts it in the right folders.
- B43/ssb driver - similar to the bcm43xx, yet it seems to work better.
- Broadcom wl - broadcom-maintained linux driver (called Broadcom STA driver by Broadcom).

Which one to use depends on your exact wireless card model.

Hope that helps a bit,
Lswest

---

### Post by Kingoftherings on 2009-05-31
> **lswest said:**
> There are 3 drivers:

- bcm43xx - this one is basically a firmware hack that rips the firmware from a .exe and puts it in the right folders.
- B43/ssb driver - similar to the bcm43xx, yet it seems to work better.
- Broadcom wl - broadcom-maintained linux driver (called Broadcom STA driver by Broadcom).

Which one to use depends on your exact wireless card model.

Hope that helps a bit,
Lswest

The Restricted Hardware Manager says Broadcom STA wireless driver.

The output of lspci says I have a bcm4312.

I did a search for broadcom wl, and I found where I can download the driver.

Thanks for the help.  :p

---

### Post by lswest on 2009-05-31
No problem, glad I could help :)

---

