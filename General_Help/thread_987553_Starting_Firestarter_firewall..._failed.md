---
title: "Starting Firestarter firewall... failed"
date: 2008-11-19
forum: General Help
---

### Post by Ubuntist on 2008-11-19
Since upgrading from Hardy to Intrepid, when I boot up one of the messages that appears as the orange progress bar is growing is

```
Starting Firestarter firewall...            [COLOR=Red]**failed**[/COLOR]
```Anybody have an idea what causes this?

Thanks....

---

### Post by mdurham on 2008-11-19
> **Ubuntist said:**
> Since upgrading from Hardy to Intrepid, when I boot up one of the messages that appears as the orange progress bar is growing is

```
Starting Firestarter firewall...            [COLOR=Red]**failed**[/COLOR]
```Anybody have an idea what causes this?

Thanks....

I think because it's already started. On my boot it stops then starts it, later on down the list it tries to start it again and reports failure. It's been doing this on my system since Hardy. You can check by running Firestarter and see if it's running. It always is for me.
Cheers, Mike

---

### Post by Ubuntist on 2008-11-20
Thanks, mdurham.  I've decided to remove Firestarter and install gufw.

---

### Post by mdurham on 2008-11-20
> **Ubuntist said:**
> Thanks, mdurham.  I've decided to remove Firestarter and install gufw.
No worries.

---

