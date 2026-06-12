---
title: "AMD 7790 driver"
date: 2013-04-15
forum: Hardware
---

### Post by contremaitre on 2013-04-15
Hi,

I just installed a recent 7790 AMD video card.
The video driver currently used is VESA.
I would like to have a better driver like radeon or fglrx, especialy to configure fan control and frequency.
What's the best choice, and how can I know what version I need to support such a recent card ?

Thank you.

---

### Post by zobo90 on 2013-04-15
I would like to know this too - got the 7770 turning up tomorrow :)

---

### Post by contremaitre on 2013-04-15
The 7770 was out one year ago, so it may already be supported with the other drivers shipped with ubuntu/
Let me know if it pick VESA like me ?

---

### Post by contremaitre on 2013-04-18
anyone ?

---

### Post by QIII on 2013-04-18
Hello!

The open source Radeon driver is included by default when you install Ubuntu.

What version of Ubuntu are you using?

It is likely that if you are using 12.04 or later, the proprietary ATI driver in the repository will work with your card.

However, the driver in the repo is fixed at the time of release, so it would not be the most recent.  It will probably work, but may not have some features a newer one would.  If you install from the repo, I would recommend that you not use the "Updates" version and that you install from the command line as described in the ATI driver link in my signature.

You can download and install the most recent version from the AMD website.  However, if you are planning to upgrade to 13.04 this month, the 13.4 driver will likely be in the repo.


Best wishes!

QIII

---

### Post by contremaitre on 2013-04-20
Actually, I am already using 13.04
But this card has less than one month, so I think the driver included in the repo does not currently suppport this card, thant's why it is not loaded for me.
So I was wondering what was the better choice, using the latest radeon driver (but how can I know when it actually support this card ?) or using the AMD one.

---

### Post by Yellow Pasque on 2013-04-20
> **contremaitre said:**
> .. the latest radeon driver (but how can I know when it actually support this card ?)

13.04 probably doesn't have full 3D acceleration without hacking some experimental components in: [http://www.phoronix.com/scan.php?page=news_item&px=MTMzODE](http://www.phoronix.com/scan.php?page=news_item&px=MTMzODE)

---

