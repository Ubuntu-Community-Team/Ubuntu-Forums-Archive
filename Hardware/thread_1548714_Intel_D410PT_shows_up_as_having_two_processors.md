---
title: "Intel D410PT shows up as having two processors"
date: 2010-08-08
forum: Hardware
---

### Post by Jeztastic on 2010-08-08
Hi,

Just upgraded my home server to an Intel D410PT - or so I thought. System Monitor is telling me I have two processors, 0, and 1. 

Have the shop sent me the dual core D510MO by mistake, and how would I tell?

Thanks!

Jez

---

### Post by chopinhauer on 2010-08-08
> **Jeztastic said:**
> 
Just upgraded my home server to an Intel D410PT - or so I thought. System Monitor is telling me I have two processors, 0, and 1. 


Atom processors with hyper-threading appear as having two processors. System Monitor will tell you exactly the model of your processor. Otherwise you can also do a ```
cat /proc/cpuinfo
```

---

### Post by Jeztastic on 2010-08-09
That's useful, thanks. So would a dual core CPU show up as 4 processors?

---

### Post by Fafler on 2010-08-09
Yes.

---

