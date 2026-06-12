---
title: "How Can I know if my Processor is 64 bit"
date: 2011-02-21
forum: Hardware
---

### Post by r_anjit on 2011-02-21
I am using a intel(R) Dual core(R) @1.67 GHz processor and wish to know whether it is 32 or 64 bit processor. Is there any wy to know that so that I may choose my operating system accordingly.

Thanks,

---

### Post by mörgæs on 2011-02-21
Yes, there are several options. You could for example run ```
hwinfo --cpu
```

---

### Post by sanderd17 on 2011-02-21
you can also take a look on wikipedia. I don't think the type of your processor is correct. if it's a core 2 duo, than it's 64bit.

[http://en.wikipedia.org/wiki/List_of_Intel_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors)

---

### Post by grahammechanical on 2011-02-21
The computer BIOS program will give you information about your machine. There should be a message on the screen as the machine boots telling what key to press to enter the BIOS program.

Regards.

---

### Post by trundlenut on 2011-02-21
type:

```
cat /proc/cpuinfo
```

into a terminal and if you see "lm" on the flags line then it is a 64bit processor.

---

### Post by KegHead on 2011-02-21
Hi!

Ailurus will give the info.

KegHead

---

