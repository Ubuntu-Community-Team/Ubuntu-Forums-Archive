---
title: "Flash drive simply named $"
date: 2010-08-24
forum: Hardware
---

### Post by ki4jgt on 2010-08-24
After I installed the upgrades this morning, every time I plug my flash drive in it's name is $. Anyone? :-O

---

### Post by clrg on 2010-08-24
Please show me the output of 

```
mount
```

I suspect the label of your USB stick's partition is wrong. If so, run

```
sudo tune2fs -L <new name> /dev/<usbstick>
```

For example:

```
sudo tune2fs -L mystick /dev/sdb1
```

---

