---
title: "Update manager"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Canuck.old on 2009-10-18
A few days ago I started the Update Manager and it 
asked me if I would like to upgrade to 9.10. I ignored that button
and installed a bunch of upgrades from 9.04.

Now the upgrade to 9.10 button won't come back.

How can I talk Upgrade Manager into asking me again?

Thank you for your time.

dkr

---

### Post by ikisham on 2009-10-18
Just wait. Next week Karmic RC1 will come out and most probably the Update Manager will offer the upgrade again.

---

### Post by Canuck.old on 2009-10-19
thanks - that is good enough

---

### Post by ikisham on 2009-10-20
The packages have already been frozen for Karmic, now it's only ironing bugs. That means, I guess, that if you upgrade then you won't have to download a lot of stuff when it goes to final (I'm using Beta and the last upgrade brought 272 MB of new stuff). Make sure you have all the updates to Jaunty, press Alt+F2 and type```
update-manager -d
```that should ask you for an upgrade to Karmic.

---

