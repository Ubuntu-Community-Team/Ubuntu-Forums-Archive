---
title: "/usr/local/lib/libcurl.so.4: no version information available"
date: 2008-08-15
forum: General Help
---

### Post by yinglcs2 on 2008-08-15
Hi,

I am getting this error:
/usr/local/lib/libcurl.so.4: no version information available

When I run transmission.

Can you please tell me how can I fix it?

Thank you.
$ transmission
transmission: /usr/local/lib/libcurl.so.4: no version information available (required by transmission)
Segmentation fault

---

### Post by ellgor on 2008-08-16
Hi,

Use synaptic (or whatever packager you use) and look for "libcurl" especially the dev bit, ie libcurl-dev, hope this helps.

Regards, Ellgor.

---

### Post by yinglcs2 on 2008-08-18
Still does not work.


$ transmission
transmission: /usr/local/lib/libcurl.so.4: no version information available (required by transmission)
Segmentation fault

---

