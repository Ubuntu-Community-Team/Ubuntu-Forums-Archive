---
title: "How to see a device serial number"
date: 2009-02-15
forum: Hardware
---

### Post by Pitboss on 2009-02-15
I want to see the serial number of my graphics controller. I tried using 

```

lspci -vvv -s xx:xx.x

```

where xx:xx.x is its location but there wasn't any serial number. So maybe I need a different command?

---

### Post by x33a on 2009-02-15
you can use lshw.

---

### Post by Pitboss on 2009-02-15
I used it but it seems that in the section "sudo lshw -class display" there doesn't appear any serial number.

---

