---
title: "Xerox B205 compatibility"
date: 2020-11-13
forum: Hardware
---

### Post by tamariskfarm on 2020-11-13
Can anyone confirm that the Xerox B205 Multifunction printer does work (as claimed) on Ubuntu 18.04? I've had bad experiences with other printers that *claimed* to work ok but actually don't have full functionallity on Ubuntu, even after downloading numerous drivers and apps. - especially the scanner failed. Xerox assure me it will work (but wont confirm what "work" means) and direct me to their driver download at [https://www.support.xerox.com/en-us/product/xerox-b205-multifunction-printer/content/145485](https://www.support.xerox.com/en-us/product/xerox-b205-multifunction-printer/content/145485) which is thin on information. Any direct experiences?

---

### Post by Doorskeeper on 2020-11-18
I have a Xerox B205 MFP working with Ubuntu 20.10. It is networked, not USB connected. The whole family uses it to print to, and I use it to scan. 
I did an upgrade from Ubuntu 18.?, and it was working just fine with version 18 also.

---

### Post by brian_p on 2020-11-18
Connect the device by wireless and give the outputs of

```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` ```
driverless
```

---

