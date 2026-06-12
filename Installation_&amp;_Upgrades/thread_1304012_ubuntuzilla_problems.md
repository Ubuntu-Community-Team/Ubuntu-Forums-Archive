---
title: "ubuntuzilla problems"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by PowerSource on 2009-10-28
i'm running ubuntuzilla.
ubuntuzilla updated just ff to 3.5.4 and now:
* I can't bookmark.
* some buttons at certain sites doesn't work, also the logo has dissapeared from that site (hamsterpaj.net)
* "webmail notifier" removed all my accounts
*some settings have been resetted
*some other small, annoying stuff

result = :(

help?

---

### Post by PowerSource on 2009-10-28
oh ****,
i read the update info at theri site. it said that i had to use gksudo instead of sudo:
> 
Note: do not use the plain sudo here. That will mess up permissions in your profile. 

what do?

---

### Post by nanotube on 2009-10-30
you probably borked up the ownership of your profile. to fix it, just run the following command:
```
sudo chown -R youruser:youruser ~/.mozilla
```

(youruser == your actual username on the computer)

that should fix you right up.

---

