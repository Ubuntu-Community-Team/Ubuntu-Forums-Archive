---
title: "startup time"
date: 2008-10-04
forum: General Help
---

### Post by unknown25 on 2008-10-04
guys i hav a problem!!!!i hav xp nd ubuntu installed in same pc....wen i startup thers only 10secs for selecting which operating system i want to use.....guys can u teach me how to increase tat time!!!!itz a big problem for me!!

---

### Post by taladan on 2008-10-04
```
sudo vim /boot/grub/menu.lst
<enter your password>
/ 10
dw
i
30
esc
:wq
<hit enter>

```

That will change your current timeout of 10 seconds to 30 seconds.  I included all the steps of using VIM in case you're not familiar with how it fuctions.

Of course you can substitute whatever amount you want instead of 30.

Hope this helps,

Tal

---

### Post by terry_gardener on 2008-10-04
install startup manager via add/remove or synaptic and then open it, under system-administration 

under the boot option tab, first section timeout select how long you want, then just click close and it make the change to the config file for you. 

hope this helps

---

