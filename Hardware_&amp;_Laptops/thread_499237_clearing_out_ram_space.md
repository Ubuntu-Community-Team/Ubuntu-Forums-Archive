---
title: "clearing out ram space"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by mr_biggie on 2007-07-12
i have read the past posts and havent found a satisfactory answer so i'll ask again. lately i have notest that my ram gets used very quickly by ubuntu. so i have 2 questions, 1 how can check what applications are hogging all the ram and 2, how do clear out the ram?

---

### Post by ironmonkeygf on 2007-07-12
1. 
terminal: use the 'top' command and see what PID is using all the RAM, noting the number
GUI: System > Administration > System Monitor

2. 
terminal: sudo kill (PID#)
GUI: kill whatever process is hogging RAM

---

### Post by tgm4883 on 2007-07-12
Linux != Windows

Your RAM usage will always be around 100% (unless you just booted).  This is by design.  Things loaded into RAM that are no longer being used stay in RAM until another program needs that space (ie you open another program and there is no available RAM).

---

### Post by az on 2007-07-12
> **mr_biggie said:**
> how do clear out the ram?

The linux kernel will flush out ram when it needs it for something else.   Basically, the kernel will not flush out buffered ram for nothing.  That would be a waste of time.  Your computer will perform better if it uses all it's ram for what it's doing - reserving ram for nothing is a waste.

Basically, linux uses ram differently than what you are used to with windows.

---

### Post by mr_biggie on 2007-07-29
ok thanks guys

---

### Post by overcaffein8d on 2007-09-13
i never thought of that...ahaha

---

