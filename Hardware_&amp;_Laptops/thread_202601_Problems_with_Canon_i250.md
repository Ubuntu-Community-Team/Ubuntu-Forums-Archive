---
title: "Problems with Canon i250"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by jrios_03 on 2006-06-23
Hi, I have a Canon i250 printer, I download an install the rpm drivers of the printer, and I install the printer this way:

```
# /usr/sbin/lpadmin -p i250 -m canoni250.ppd -v canon_usb:/dev/usblp0 -E
# /usr/sbin/lpadmin -d i250
```

and in Firefox I go to [http://localhost:631/printers](http://localhost:631/printers), and it show me the Printer...

But, when I try to print, the page gives me this error:
```
"/usr/lib/cups/backend/canon_usb failed"
```

I send you an Image with the screenshoot

Please help me...

---

