---
title: "Graphics Card Problems"
date: 2009-07-14
forum: Hardware
---

### Post by mykeljee on 2009-07-14
Hi, I just installed Ubuntu Jaunty and I'm having some trouble... My current graphics card is a GeForce Go 6150 and when I go to System>Administration>Hardware Drivers: my card isn't recognized. There's nothing there except for my wireless card, so I can't apply any drivers. How did this happen? I've installed Ubuntu on this machine before and it recognized everything fine.

---

### Post by overdrank on 2009-07-14
> **mykeljee said:**
> Hi, I just installed Ubuntu Jaunty and I'm having some trouble... My current graphics card is a GeForce Go 6150 and when I go to System>Administration>Hardware Drivers: my card isn't recognized. There's nothing there except for my wireless card, so I can't apply any drivers. How did this happen? I've installed Ubuntu on this machine before and it recognized everything fine.

Hi and welcome, you may need to update your system. You can use the terminal and enter this command ```
sudo apt-get update && sudo apt-get upgrade
``` The terminal is located under applications, accessories.
You mays also use update manager located under system, administration.

---

### Post by mykeljee on 2009-07-15
Thanks! I guess the repositories just needed to be updated.

---

