---
title: "i need my vga driver"
date: 2008-11-30
forum: Hardware
---

### Post by trazan2010 on 2008-11-30
[B][CENTER]my vga is [COLOR="Red"]plug and play monitior on s3 garphics prosaveage ddr[/COLOR]
can any one help me to find a driver fotit[/CENTER][/B]

---

### Post by trazan2010 on 2008-12-01
any heeeeeeeeeelp

---

### Post by overdrank on 2008-12-01
> **trazan2010 said:**
> [B][CENTER]my vga is [COLOR="Red"]plug and play monitior on s3 garphics prosaveage ddr[/COLOR]
can any one help me to find a driver fotit[/CENTER][/B]

Hi and what version of Ubuntu are you using? If you are using Hardy 8.04, you can try the command ```
gksu displayconfig-gtk
``` and adjust there. The S3 graphics are not well supported. If the above command fails you can try the xfix option while booting into recovery mode which is usually the second choice at the grub.

---

### Post by trazan2010 on 2008-12-01
> **overdrank said:**
> Hi and what version of Ubuntu are you using? If you are using Hardy 8.04, you can try the command ```
gksu displayconfig-gtk
``` and adjust there. The S3 graphics are not well supported. If the above command fails you can try the xfix option while booting into recovery mode which is usually the second choice at the grub.
** i am using 8.10**

---

### Post by overdrank on 2008-12-01
> **trazan2010 said:**
> ** i am using 8.10**

Then all I can suggest is trying the xfix option I mentioned in my earlier post.

---

