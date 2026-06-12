---
title: "System information"
date: 2009-03-06
forum: Hardware
---

### Post by joshaman on 2009-03-06
Does anyone know of a program comparable to Everest or Sandra for Ubuntu?  Those programs wouldn't work too well at detecting hardware through Wine, would they?  

I want to check out my UDMA speeds and I want to see if HPET is enabled.

---

### Post by sdennie on 2009-03-06
lshw is generally useful for figuring out what is inside a machine:

```

sudo lshw

```

Looking through the logs is also very useful.  For the two specific questions you are asking, try:

```

dmesg | grep -i udma
dmesg | grep -i hpet

```

Also, better info for the udma can be found with hdparm:

```

sudo hdparm -I /dev/sda

```

---

### Post by joshaman on 2009-03-07
Thank you *very* much.

---

