---
title: "Asus P5B Error 21"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by puner on 2009-03-03
Hello

I have one 120gb IDE drive in my computer, with other drives unplugged as well as the dvd drive. I installed ubuntu on the IDE, and everything went fine.

When I finally rebooted I got error 21.

-Thanks

---

### Post by cariboo on 2009-03-03
Your drive order has changed since you plugged in your other drives. Could you boot from the LiveCD and open a Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

and paste the output in your next post, you can do this while running the LiveCD.

Jim

---

### Post by puner on 2009-03-03
I did not plug in the other drives yet

---

