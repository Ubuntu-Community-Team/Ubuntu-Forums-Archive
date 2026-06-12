---
title: "Can't find driver for my Laptop!?"
date: 2009-09-01
forum: Hardware
---

### Post by Goksu Toprak on 2009-09-01
Hello everyone!

I have FSimens Esprimo Mobile V5535 Laptop and my laptop's graphic details;

SiS Mirage 3+ Graphics, 64-256 MB Shared Memory.

I can't find any driver and I need your help.I stuck with 800*600 resolution and my videos not perform well.

Regards.

---

### Post by newton21989 on 2009-09-03
Does this link help? [http://www.sis.com/download/agreement.php?url=/download/](http://www.sis.com/download/agreement.php?url=/download/)

---

### Post by Goksu Toprak on 2009-09-05
> **newton21989 said:**
> Does this link help? [http://www.sis.com/download/agreement.php?url=/download/](http://www.sis.com/download/agreement.php?url=/download/)
  
Unfortunately  No,

Because I can use these files.

There's no application to use that files.

---

### Post by IcarusR on 2009-09-05
Downloaded file is .rpm file, you need to use alien to convert to .deb.

```
sudo apt-get install alien
sudo alien  /path/to/file.rpm
```

Checkout the alien manpage

```
man alien
```

---

