---
title: "DVD not recognized Ubuntu 9.10"
date: 2010-02-01
forum: Hardware
---

### Post by romina17 on 2010-02-01
Hi, 
Ubuntu 9.10 does not recognize my DVD.. I used to have Ubuntu 9.04 and it recognized it just fine.. I am new on this, can somebody help???

Thanks!

---

### Post by hemimaniac on 2010-02-01
DVD drive or DVD Disc?

---

### Post by wojox on 2010-02-01
Try:

```
sudo apt-get install libdvdread4
```

Then:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by romina17 on 2010-02-01
that solved it, thanks!!!!!! :)

---

### Post by charlieab1 on 2011-02-19
brill that did the job for me too 

many thanks

---

