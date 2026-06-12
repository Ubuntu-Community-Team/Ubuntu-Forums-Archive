---
title: "amilo Pi 1536 not finding modem with kubuntu 6.06"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by mad_alfred on 2006-11-07
hi everyone!!

i just bought a laptop as in the threa name and since i prefer kubuntu to windows XP I installed the latest version i had at home : kubuntu 6.06

My problem regards the modem, in windows it shows up in com3 but i can't find it in kubuntu with wvdialconf. the modem is integrated.

what shall i do??

thanks in advance for the help :)

---

### Post by dentaku65 on 2006-11-11
Try this:

```
sudo apt-get install sl-modem-daemon sl-modem-source
```
and I think you'll solve the problem :cool:

---

