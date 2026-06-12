---
title: "Gutys Not Recognizing USB Flash Drives"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by k1dicarus on 2008-02-02
I hope I'm posting in the correct location..

I used to run Ubuntu Fesity on my Toshiba M45-S359 laptop, and it could recognize my USB flash drives just fine. I updated to Gutsy and love every minute of it... except for the fact that it just will not recognize my USB flash drives. Anyone else having this issue? I checked the IRC and no one had ever encountered this.

Thanks!

---

### Post by cdtech on 2008-02-03
Do you have any error messages from your "dmesg" command run in a terminal after connecting a USB device?

```
dmesg | grep usb
```

Do you see your modules loaded?

```
lsmod | grep usb
```

---

