---
title: "Is there software to test USB-Sticks for errors?"
date: 2008-10-31
forum: Hardware
---

### Post by SRTS on 2008-10-31
Hi, I have an USB-Stick which I suspect to have faulty flash memory.
Are there any tools for ubuntu that I can use to test it?

---

### Post by hardyn on 2008-10-31
they are so cheap now, does it matter?

---

### Post by SRTS on 2008-10-31
> **hardyn said:**
> they are so cheap now, does it matter?

It does matter however, whether the brain is enabled before posting.

---

### Post by hardyn on 2008-11-04
"gee hardyn, i know they are cheap; but i would like scan my disk anyway"

try a "badblocks" from the command line, the manual does not explicitly state it will work with solid state media, but it does not say that they wont either. if you use the write test, you should be able to determine if your disk has serious write errors.

$ man badblocks 

if you need more info.

---

