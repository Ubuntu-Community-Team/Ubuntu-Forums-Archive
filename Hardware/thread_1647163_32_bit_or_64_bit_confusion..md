---
title: "32 bit or 64 bit confusion."
date: 2010-12-16
forum: Hardware
---

### Post by Nath4n on 2010-12-16
I know this is going to be a stupid question.  I have an Acer Aspire One D255 with an Intel n450 Atom processor.  On Intels site about this chip it states that the instruction set is 64 bit.  Does this mean I need to be running 64 bit Ubuntu?  How can I tell which version I am running? And would there be a significant difference in the system?  Sorry if this is a dumb questions.  I would really appreciate someone clearing this up for me.

---

### Post by Yellow Pasque on 2010-12-16
You don't need to run 64-bit (but you can if you wish).

> How can I tell which version I am running?
```
uname -a
```
If you see amd84 or x86_64, then you're running 64-bit. If you see i686 or i386, 32-bit.
Also, see: [https://help.ubuntu.com/community/32bit_and_64bit/](https://help.ubuntu.com/community/32bit_and_64bit/)

---

### Post by Nath4n on 2010-12-17
Aha.  I see.  Well I will for sure not be doing any tasks that will require 64 bit processing. I was under the impression that 64 bit would make my computer twice as fast.  Thanks for the info and the link!

---

### Post by cascade9 on 2010-12-17
> **Nath4n said:**
>  I was under the impression that 64 bit would make my computer twice as fast.  Thanks for the info and the link!

For some things, 64bit is near enough to tiwce as fast. For most tasks, its in the order of 5-15% faster.

---

