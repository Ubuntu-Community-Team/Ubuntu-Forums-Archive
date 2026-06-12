---
title: "Accessing internal machines from outsite"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by paulfox on 2006-01-12
Hi all,
We have 3 printers each with an IP address on our internal network.
The software used to connect to the printers uses port 3001,
so internally for printer one you'd use:
```

192.168.1.171 port 3001

```
however there are 3 printers (.171, .172, .173) and i need to access them from outside.
Will this work:
from outside, to access printer one use:
213.155.153.82 port 171
and on the internal network, port forward port 171 to the 192.168.1.171 machine? and do the same for the 2 other printers.

any help/ideas would be great!

---

