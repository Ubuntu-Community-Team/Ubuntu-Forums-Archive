---
title: "suspend broken after sept.19 update..."
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2006-09-22
any ideas what happened and how to get it back?

thanks.

asus z70va notebook.

---

### Post by berg82 on 2006-09-22
It seems I have the same problem. The system freezes when I try to resume.

---

### Post by hardyn on 2006-09-22
the graphics screen fails to return and says something about 

cmd 12 failed

and unexpected bus power failure...

i tried the old kernel as well and problem persists, so its not in the kernel but another module that was involved in that update.

anybody submitted a bug report on this one.

---

### Post by berg82 on 2006-09-23
Yeah, The graphics fail to load after resume. 
Is there any chance we can get information of wich packages that was included in this update?

hardyn > Have you submitted a bug report on this? 

I have an Fujitsu Amilo M7400.

---

### Post by berg82 on 2006-09-23
Hey, 

I installed the updates today and now the problem is fixed! 

Good Job! I Love Ubuntu!

---

### Post by hardyn on 2006-09-23
yes a bug report was filed.

---

### Post by xyz on 2006-09-23
I followed this howto to suspend...in case anyone is interested. I can suspend in less than 2 seconds running:
```
 echo -n mem > /sys/power/state

```

---

