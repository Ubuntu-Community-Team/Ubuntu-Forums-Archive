---
title: "Update to 8.04.2?"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by ScottEChapman on 2009-03-01
I am running 8.04 on a couple of VMs. There apparently was some issue with VMI support that *might* be fixed in 8.04.1.

I see that 8.04.2 is out.

What is the process for updating my system to the latest version of 8.04.2?

Sorry if this is an obvious noob question...

---

### Post by whoop on 2009-03-01
If you are keeping your 8.04 up to date in the normal manner (update manager, apt-get) you will now have 8.04.2
No special upgrade path is needed.

---

### Post by ScottEChapman on 2009-03-01
Yup, update manager says I am up to date.

Is there an easy way to confirm which release I am at (something that would show 8.04.2)?

---

### Post by whoop on 2009-03-01
Don't know. Maybe  
```

lsb_release -r

```
what does that output?

---

### Post by ScottEChapman on 2009-03-02
command not found.

---

### Post by jespdj on 2009-03-02
try this:
```
cat /etc/issue
```
It should say 8.04.2.

---

