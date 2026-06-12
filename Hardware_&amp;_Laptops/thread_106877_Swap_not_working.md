---
title: "Swap not working"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by migueljacq on 2005-12-21
Someone please move this if it's in the wrong forum but I couldn't decide on a suitable category.

I've got a laptop running Ubuntu, but my swap isn't working. It's allocated a certain amount of memory to the swap partition, but it is not using it, and the main memory is overloaded as a result. Does anyone know a solution for this?

Cheers
Miguel

---

### Post by towsonu2003 on 2005-12-21
after checking if swap is in use ```
free -m
```try doing this ```
sudo swapoff -a
sudo swapon -a
```
these will turn off and on the swap, may be that could help? If that doesn't help, posting the output of ```

free -m
sudo fdisk -l
``` might help others assist you (as it will be over my head then).

---

