---
title: "software for identifying hardware vendors"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by wpshooter on 2007-08-23
Is there a software utility application in Ubuntu that will allow me to know what the vendor/manufacturer of the memory/RAM being used in the computer is without having to take the memory out of the machine ?

Thanks.

---

### Post by heimo on 2007-08-23
> **wpshooter said:**
> Is there a software utility application in Ubuntu that will allow me to know what the vendor/manufacturer of the memory/RAM being used in the computer is without having to take the memory out of the machine ?

Unlikely. Can it be done in any system? Does normal memory modules support this kind of feature? I don't think so. I've never seen it. (*


*) EDIT: I know memory modules communicate some information to your system, timings, but don't know if there's any other information available

---

### Post by Dark Star on 2007-08-23
Try this 
```
sudo lshw
```

---

### Post by wpshooter on 2007-08-23
> **Dark Star said:**
> Try this 
```
sudo lshw
```

Well, unfortunately this gives the vendor name for about every component except the one I am looking for (the memory).

Thanks, anyway.

---

