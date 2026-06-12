---
title: "Hardware_ECC_Count  what is this ?"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by cherva on 2008-01-20
What exactly is Hardware_ECC_Recovered  showed by smartctl -a ? And is there a problem if  a HDD ( 1 month old ) has 
```

195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       697529

```
OK 
After an  Extended offline test :
```

195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       19523350

```
WHAT IS HAPPENING ?!
This HDD is working for 720 hours....

---

### Post by cherva on 2008-01-25
OK no one knows what a Hardware_ECC_Count is ?

---

### Post by Yellow Pasque on 2008-01-25
ECC = Error Correcting Code. Basically, your HD tried to read/write something and the data  wasn't the same on the controller side as it was on the disk side, so it sent data again and everything was good.

I'm not sure how to interpret the values offhand, but if there is a problem, the first thing I would check is the cable, especially if it's a Parallel ATA (PATA) ribbon cable. Make sure you're using an 80-pin cable as short as possible (18" max is the IEEE spec) without any overlapping folds.

---

