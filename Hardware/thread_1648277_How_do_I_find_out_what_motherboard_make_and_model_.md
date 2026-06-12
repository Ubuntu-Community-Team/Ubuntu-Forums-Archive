---
title: "How do I find out what motherboard make and model do I have?"
date: 2010-12-18
forum: Hardware
---

### Post by Ederico on 2010-12-18
Dear all,

I'm running Ubuntu 10.10. Is there a way for me to discover my motherboard model and make through such an OS and if yes, how?

Thanks beforehand for any help attempted and/or given.

Best regards,
Ederico.

---

### Post by matt-fender on 2010-12-18
Try 

```
lspci
``` in a Terminal, should give you some more information regarding chipset etc

---

### Post by akand074 on 2010-12-18
lspci only lists hardware attached to your pci ports. Type this into a terminal

```
sudo dmidecode | more
```Scroll down a bit using the return button to get more until you find "Base Board Information".

---

### Post by Ederico on 2010-12-18
There's a Base Board Information, I guess that's it. There's no System Board Information. Thanks.

---

### Post by akand074 on 2010-12-18
> **Ederico said:**
> There's a Base Board Information, I guess that's it. There's no System Board Information. Thanks.

Yeah sorry I immediately corrected it. That's it.

---

### Post by Ederico on 2010-12-18
Thanks a lot. :)

---

