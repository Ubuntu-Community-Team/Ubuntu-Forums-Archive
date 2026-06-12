---
title: "How to switch off internal speaker on HP TX1000"
date: 2009-07-25
forum: Hardware
---

### Post by Aura21 on 2009-07-25
hey guys, i just need to know the command on how to switch off my internal speaker on my HP TX1000, the reason is each time i switch off my laptop, it will make this loud short noise, like a "BEEEPPPPP", it sooo annoying, this only happened when i upgraded to Ubuntu 9.04, please help.....:confused:

---

### Post by mikewhatever on 2009-07-25
Run the following command in Terminal: **sudo modprobe -r pcspkr**.
If it works as expected, make the change permanent with the command below.
**sudo echo blacklist pcspkr >> /etc/modprobe.d/blacklist.conf**

---

