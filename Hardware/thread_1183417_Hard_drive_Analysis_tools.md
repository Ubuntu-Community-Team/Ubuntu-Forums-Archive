---
title: "Hard drive Analysis tools"
date: 2009-06-10
forum: Hardware
---

### Post by Goddard on 2009-06-10
I want more information on the drives in my computer.  Anyone know of some good utils?

---

### Post by cariboo on 2009-06-10
Hdparm, which is installed by default is a good tool. Open an Applications-->Accessories-->Terminal and type:

```
sudo hdparm -tT /dev/sda
```

the above command will print out the dreives transfer speeds. For more info see:

```
man hdparm
```

---

