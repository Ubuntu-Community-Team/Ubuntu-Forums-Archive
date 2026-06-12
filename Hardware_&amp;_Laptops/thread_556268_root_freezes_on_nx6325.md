---
title: "root freezes on nx6325"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by fauntumnus on 2007-09-21
hi, 
i've installed feisty fawn on compaq nx6325.
everything works fine, wireless works well, no problem in audio drivers even bluetooth is ok. 
but when i log in as root to configure my sourcelist, everything freezes, nothing responds (no problem as i log in as user)
why could it be?

---

### Post by eggdeng on 2007-09-21
Can you edit your sources.list using sudo? ```
sudo gedit /etc/apt/sources.list
```
> when i log in as root
Are you talking about graphical login? Have you set a root password?

---

### Post by fauntumnus on 2007-09-22
yes, graphical log in, i changed the root password but after log in, everything freezes.
by the way thanks fot gedit tip :) that way i was able to configure my sourcelist

---

