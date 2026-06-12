---
title: "hdparm, get values previously set by -S or -B"
date: 2009-02-11
forum: Hardware
---

### Post by raaboof on 2009-02-11
Hello all, does anyone know if there is a way to check current values of APM mode and Standby timeout active for a certain drive? These are the values set by using hdparm -B and hdparm -S commands.

The way OS is setting these values during/after boot is not very simple, so I would like to be able to check what the actual values after boot are.

-Petteri Heinonen

---

### Post by empty_spaces on 2009-02-11
Not sure about hdparm -S, but I think
**sudo hdparm -I /dev/sda | grep -i power**
should give you the hdparm -B value

---

### Post by raaboof on 2009-02-12
Unfortunately, no it doesn't:

root@host:~# hdparm -I /dev/sda | grep -i power
           *    Power Management feature set
root@host:~#

This really bothers me, as for several other hdparm options there are both set and get methods. But not for -S and -B, which are probably one of the most used options to tune hard drive behavior. Well, it is not just possible to query these values from the hardware.

---

