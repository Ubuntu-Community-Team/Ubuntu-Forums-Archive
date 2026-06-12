---
title: "no sound after update 3rd time..."
date: 2008-08-26
forum: General Help
---

### Post by Mia_tech on 2008-08-26
it's been the 3rd time that I'm left without sound after an update....is there anyone experience the same problems?


thanks

---

### Post by iaculallad on 2008-08-26
> **Mia_tech said:**
> it's been the 3rd time that I'm left without sound after an update....is there anyone experience the same problems?


thanks

Was it a kernel update? Try to install the generic file:

```
sudo apt-get install linux-generic
```

---

### Post by Mia_tech on 2008-08-27
tried that too
```
jorge@ubuntu-box:~$ sudo apt-get autoremove
[sudo] password for jorge: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

no help there

---

