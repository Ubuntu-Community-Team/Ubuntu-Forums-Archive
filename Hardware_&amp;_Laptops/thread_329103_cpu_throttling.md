---
title: "cpu throttling"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by lcaley on 2006-12-31
Hi. I have recently gotten my dual core support to work, but my second processor is only showing at 50%. It isn't responding to my performance profiles that I have set, but the first one still is. Is there something I have to do to tell the power management software to look for two processors now? Or is there a shell command I can type to check on the frequency of my cpu's?

Thanks.

---

### Post by jvc26 on 2008-02-05
```

cat /proc/cpuinfo

```

Will give you the data on your cpu

Il

---

