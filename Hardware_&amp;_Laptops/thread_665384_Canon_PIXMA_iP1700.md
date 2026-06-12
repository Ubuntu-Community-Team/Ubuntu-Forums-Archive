---
title: "Canon PIXMA iP1700"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by GhentK on 2008-01-12
Hi all,

I have an iP1700 that worked great under Feisty. When I updated to Gutsy (re-format), however, I lost the driver for the printer, as I thought that I could merely re-download it. I know that I'm supposed to use the [iP2200 drivers](http://software.canon-europe.com/products/0010231.asp), but, as it turns out, the drivers on that page are for the iP4200 that do not work for my iP1700.

Does anyone know where I can find the original 2.60-iP2200 drivers, or can someone maybe send them to me?

Thanks. :)

---

### Post by Sef on 2008-01-12
Read OpenPrinting's solution to get the [Pixma iP1700]("http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700") to partially work.

---

### Post by GhentK on 2008-01-13
> **Sef said:**
> Read OpenPrinting's solution to get the [Pixma iP1700]("http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700") to partially work.
I have read the description and changed the maxmediawidth and -height (although it wasn't necessary under Feisty) to no avail. The link on the page to the iP2200 drivers leads to the iP4200 drivers that cannot drive the printer as I wrote in my post.

The problem is "cups-missing-filter" (according to the printer manager). I suspect that it is because the iP4200 filter doesn't work, and that's why I'd like the iP2200 filter. It is no longer available through Canon, though.

---

### Post by GhentK on 2008-01-13
Ah, it's in the tar ball on Canon's homepage; I thought that it would be the source code. *smacks head*

---

