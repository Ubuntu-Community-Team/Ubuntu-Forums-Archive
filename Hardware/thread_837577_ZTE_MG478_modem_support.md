---
title: "ZTE MG478 modem support"
date: 2008-06-22
forum: Hardware
---

### Post by AlexeyTyapkin on 2008-06-22
Hello All,
I've add product and device ids to airprime module:
```
        { USB_DEVICE(0x19d2, 0xfffe) }, /* ZTE MG478 */
```

So speed improved a little from 60Kb(while using usbserial) up to 100Kb. But I want to have full speed EvDO transfers (2.4Mb download/ 750Kb upload). Any idea how to get it? 

P.S.: Dear developers please add support of this device to airprime module.

---

