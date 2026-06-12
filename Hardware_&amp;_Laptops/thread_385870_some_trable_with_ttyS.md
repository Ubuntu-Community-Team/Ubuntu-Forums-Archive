---
title: "some trable with ttyS*"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by Attid on 2007-03-16
one mashine don`t get me to connect to ttyS*
i can use sudo but than i mast always enter my password
how can i set rights to than?




next trable when i use ubuntu 6.06 after install
ls /dev/ttyS*
print to me ttyS0-ttyS40
when i install ubuntu 6.10
ls /dev/ttyS*
print to me ttyS0-ttyS3
whan i can back my serial port ?

---

### Post by Attid on 2007-03-23
whan i rollback to  2.6.15-27-386 kernell and all start work =)
now i have all 48 serial port

i don`t know what is it, error or in kernel 2.6.17 and upper mast be another way 
but i try  install 2.6.20 kernel from kernel.org ant it not help me.

some body can to say some about it ?

---

### Post by Attid on 2007-03-26
:popcorn: 
if 2.6.17 and upper then 
good idia will be 

```
#nano /boot/grub/menu.lst
```

find string with your kernel

```
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=fb86a7ac-$
```

and add there 8250.nr_uarts=8 (or 8250.nr_uarts=16 if you want 16 serial port)

```
kernel          /boot/vmlinuz-2.6.17-11-386 8250.nr_uarts=8 root=UUID=fb86a7ac-$
```

and after reboot you get 
```
# ls /dev/ttyS*
/dev/ttyS0  /dev/ttyS2  /dev/ttyS4  /dev/ttyS6
/dev/ttyS1  /dev/ttyS3  /dev/ttyS5  /dev/ttyS7

```

---

