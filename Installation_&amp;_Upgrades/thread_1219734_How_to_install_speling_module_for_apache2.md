---
title: "How to install speling_module for apache2"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by sharif_aly on 2009-07-22
How to install speling_module for apache2 ?

I have try to look in synaptic but no luck finding the mod .. if you find it please tell me the name in synaptic or how exactly I can install it ?

```
#LoadModule speling_module

Attempts to correct mistaken URLs that users might have entered by ignoring capitalization and by allowing up to one misspelling
```

---

### Post by yeats on 2009-07-22
According to the Apache website, it looks like this module should be on board:

CheckSpelling was available as a separately available module for Apache 1.1, but was limited to miscapitalizations.** As of Apache 1.3, it is part of the Apache distribution.** Prior to Apache 1.3.2, the CheckSpelling directive was only available in the "server" and "virtual host" contexts.

from [http://httpd.apache.org/docs/2.2/mod/mod_speling.html](http://httpd.apache.org/docs/2.2/mod/mod_speling.html)

---

