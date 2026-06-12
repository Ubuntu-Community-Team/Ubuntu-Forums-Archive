---
title: "error in update manager"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by glynn on 2009-01-29
I have just had an error when I try to install updates recommended in 8.04 - see screenshot for the exact error.  It offers a way to correct the eror, but I am not sure how to do what is being asked.  Help please.

---

### Post by n2dabloo on 2009-01-29
I'm having an update issue as well: 
[IMG]http://f.imagehost.org/0350/Screenshotupdatefail.png[/IMG]

---

### Post by Partyboi2 on 2009-01-29
> **n2dabloo said:**
> I'm having an update issue as well: 

Make sure you are only using one package manager at a time eg update manager, synaptic....

> **glynn said:**
> I have just had an error when I try to install updates recommended in 8.04 - see screenshot for the exact error. It offers a way to correct the eror, but I am not sure how to do what is being asked. Help please.
Open a terminal (Applications>Accessories>Terminal) and do as suggested
```
sudo dpkg --configure -a
```

---

### Post by Partyboi2 on 2009-01-29
deleted

---

### Post by n2dabloo on 2009-01-29
I simply rebooted and it seems to work fine now ;)  Thanks

---

