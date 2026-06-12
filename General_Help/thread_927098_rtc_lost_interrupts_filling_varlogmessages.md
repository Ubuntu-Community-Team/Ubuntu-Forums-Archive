---
title: "rtc lost interrupts filling /var/log/messages"
date: 2008-09-22
forum: General Help
---

### Post by tlacuache on 2008-09-22
Since I installed Hardy on my new Dell Precision M6300 laptop, my /var/log/messages is full of this sort of thing:

```
Sep 22 14:17:28 tlacuache-laptop kernel: [203086.738750] rtc: lost 9 interrupts
Sep 22 14:17:36 tlacuache-laptop kernel: [203094.483527] rtc: lost 9 interrupts
Sep 22 14:17:40 tlacuache-laptop kernel: [203097.959460] rtc: lost 9 interrupts
Sep 22 14:17:44 tlacuache-laptop kernel: [203101.399833] rtc: lost 14 interrupts
Sep 22 14:17:52 tlacuache-laptop kernel: [203108.554529] rtc: lost 13 interrupts
Sep 22 14:17:56 tlacuache-laptop kernel: [203112.261169] rtc: lost 9 interrupts
Sep 22 14:18:08 tlacuache-laptop kernel: [203123.671539] rtc: lost 15 interrupts

```

The laptop runs fine, I'm not sure what the problem is, but the constant messages are a pain. Any ideas on how I can either get rid of the warning or at least change syslog.conf somehow to just throw these away?

-SG

---

### Post by tlacuache on 2008-09-22
I forgot to mention:
```
$ cat /proc/sys/dev/rtc/max-user-freq 
64
```

---

### Post by fooey on 2009-03-09
Would like to know how to stop/filter these as well. Thanks

---

### Post by fooey on 2009-03-17
no one....?
:?:

---

### Post by fooey on 2009-03-29
:confused:

---

