---
title: "Network Admin"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2009-01-15
For 8.10, when the computer name is changed, which files are updated? 

I tried manually changing the computer name in /etc/hosts. However, subsequent sudo commands complained that the original computer name could not be resolved.

---

### Post by cariboo on 2009-01-15
To change your computers host, in a terminal type:

```
hostname <new_hostname>
```

The change will not take effect until you reboot.

You can alias your hostname to almost anything you want in /etc/hosts.

Jim

---

### Post by cmnorton on 2009-01-15
> **cariboo907 said:**
> To change your computers host, in a terminal type:

```
hostname <new_hostname>
```The change will not take effect until you reboot.

You can alias your hostname to almost anything you want in /etc/hosts.

Jim

Thanks

---

### Post by albinootje on 2009-01-15
> **cmnorton said:**
> For 8.10, when the computer name is changed, which files are updated? 


Apart from /etc/hosts there's also /etc/hostname to think about.
Adjusting that properly too, then after a reboot all should be fine.

---

