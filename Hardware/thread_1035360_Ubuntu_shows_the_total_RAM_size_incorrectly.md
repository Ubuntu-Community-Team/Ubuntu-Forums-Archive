---
title: "Ubuntu shows the total RAM size incorrectly"
date: 2009-01-09
forum: Hardware
---

### Post by sasanpad on 2009-01-09
Hi All,

I've got a Sony Vaio FW21M laptop which has 4GB of RAM. In Vista the total RAM size is set to 4GB as expected but in Ubuntu the total RAM size is 2.9GB. 
Does anyone know why that is like that?

Thanks in advance
Sassan

---

### Post by taurus on 2009-01-09
Did you install the 32bit version of Ubuntu?

Applications -> Accessories -> Terminal
```
uname -a
free -m
```

---

### Post by sasanpad on 2009-01-09
Yes I have the 32 bit version.

---

