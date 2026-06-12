---
title: "unknown setting (0x80fe)"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by gubemton on 2008-02-16
For some reason, my laptop refuses to set its Advanced Power Harddisk mode into 225.  I dont know why.

```
slyf@lappy /usr/share $ sudo hdparm -I /dev/sda|grep Advanced
        Advanced power management level: unknown setting (0x80fe)
           *    Advanced Power Management feature set
slyf@lappy /usr/share $ sudo hdparm -B 255 /dev/sda

/dev/sda:
 setting Advanced Power Management level to disabled
slyf@lappy /usr/share $ sudo hdparm -I /dev/sda|grep Advanced
        Advanced power management level: unknown setting (0x80fe)
                Advanced Power Management feature set
slyf@lappy /usr/share $ sudo hdparm -B 254 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
slyf@lappy /usr/share $ sudo hdparm -I /dev/sda|grep Advanced
        Advanced power management level: unknown setting (0x80fe)
           *    Advanced Power Management feature set

```

Thanks, Slyf

---

### Post by gubemton on 2008-02-16
Just an update, the reason I am asking is because sometimes I have an issue with the hdd just stopping, and clicking like mad.

---

