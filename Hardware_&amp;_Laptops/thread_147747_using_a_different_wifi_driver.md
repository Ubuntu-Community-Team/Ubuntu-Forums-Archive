---
title: "using a different wifi driver"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by aztektum on 2006-03-20
I have a USR 5410 wifi card that will use the native ACX driver. However it lacks WPA support and the card will work with NDIS, but the ACX driver seems to be taking over and loading when the card is inserted. How can I disable the ACX driver?

---

### Post by dragomirov on 2006-03-20
I suppose you're telling about the kernel driver so:

```
lsmod |grep acx
```

finds the kernel module loaded for your card

```
sudo rmmod *modulename*
```

removes it

h&k

---

### Post by aztektum on 2006-03-20
brilliant. thanks.

---

### Post by dragomirov on 2006-03-20
;)

---

