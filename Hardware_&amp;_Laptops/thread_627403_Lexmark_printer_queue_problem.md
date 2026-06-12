---
title: "Lexmark printer queue problem"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by gorgor_bay on 2007-11-30
Hi all,

I've got a Lexmark T630 out on the local network over ehere at the office.
So I've downloaded the driver from Lexmark (deb file) and installed it. Then I added a device.
Now I have to add a printing queue, but unfortunately it seems impossible, I get the error:
```
"Creating print queue xxxxx failed."
```

This error was already seen here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

The fix for that was changing the ownership of /etc/cups/interfaces.
The problem with gutsy is that it is impossible, I get the error:
```
chown: `cupsys.lp': invalid user
```

Plus the interfaces folder actually does not exist.
Any idea?

---

### Post by gorgor_bay on 2007-12-03
*bump*

---

