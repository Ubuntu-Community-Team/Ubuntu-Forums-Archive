---
title: "Fan not working correctly in 12.10"
date: 2013-02-08
forum: Hardware
---

### Post by avoliva on 2013-02-08
I have Toshiba Satellite L350, with a Mobility Radeon HD 3100 GPU.

When I'm on Windows and my computer heats up, you can hear the fan whirl and it cools off. However, when using Ubuntu 12.10, my computer heats up pretty bad (90C sometimes) and you can't even hear the fan working. I can see that it's running, but it seems to be on low speed. After a while, my laptop will just shut off. I'm pretty sure it's my GPU that gets really hot for whatever reason. Anyone know what's going on here? Obviously my fan works correctly, because in Windows you can hear it.

---

### Post by Mark Phelps on 2013-02-08
You need to know that AMD dropped Linux driver support this summer for their HD 2x/3x/4x series cards such that their restricted driver will NOT work with these cards in Ubuntu 12.10.  So, you're relegated to using the open source Radeon driver, and that does not provide GPU temp controls the way the restricted driver did.

It will, however, work with the cards in Ubuntu 12.04.

---

