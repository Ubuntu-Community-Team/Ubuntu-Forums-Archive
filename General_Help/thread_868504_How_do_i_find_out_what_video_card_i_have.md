---
title: "How do i find out what video card i have?"
date: 2008-07-23
forum: General Help
---

### Post by Rickyk on 2008-07-23
How do i find out what video card i have?? im running Ubuntu 8.04

Thanks,
Ricky

---

### Post by tuxxy on 2008-07-23
Application > SYstem Tools > Sysinfo will display all your system information.

---

### Post by Rickyk on 2008-07-24
there is system info option

---

### Post by overdrank on 2008-07-24
> **Rickyk said:**
> there is system info option

You may also use the command ```
lspci
``` and look for VGA. 
More detailed if can be obtained with the command ```
lshw
```
Sysinfo also you can install via synaptic manager or the command ```
sudo apt-get install sysinfo
``` you can replace apt-get with aptitude if you prefer.
Moved to General help.

---

### Post by angry_johnnie on 2008-07-24
```
lspci | grep VGA
```

lspci alone lists everything.

---

### Post by coffeecat on 2008-07-24
> **tuxxy said:**
> Application > SYstem Tools > Sysinfo will display all your system information.

Not unless you install sysinfo first. :wink:

---

