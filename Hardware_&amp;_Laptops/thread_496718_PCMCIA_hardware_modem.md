---
title: "PCMCIA hardware modem"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by sanoj on 2007-07-09
I got a hardware modem Zonet PCMCIA v.92 56k. The card works and I can dial up my ISP problem (I'm writing this note with such a connection). But I have a problem:

1. My computer only sometimes detect my modem when I boot Ubuntu. Unplugging and plugging in again does not solve the problem, I have to re-boot the computer one or two times. I detect this using the wvdialconf tool on /dev/ttySX. What I want is naturally for my PCMCIA card to be detected always.

Also small questions:

2. Occasionally my modem starts making loud "noise" sounds when I am surfing.
a) How do I turn it off?
b) Is there anything I can do to block the kernel from allowing the sound?

3. How do I check what speed I am connected with?


Running 7.04 feisty fawn. Help appreciated!




EDIT:
The messages I get when it fails to detect the modem are something like:
```

ttyS0: failed with 2400 baud, next try: 9600 baud
ttyS0: failed with 9600 baud, next try: 115200 baud
ttyS0: and failed too at 115200, giving up.

```

---

### Post by sanoj on 2007-07-09
I also just noticed that the card seems to be detect the third time I boot (2nd reboot, that is). It seems to me like a strange coincidence.

---

