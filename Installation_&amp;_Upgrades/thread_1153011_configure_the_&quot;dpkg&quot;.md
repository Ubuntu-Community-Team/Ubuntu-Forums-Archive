---
title: "configure the &quot;dpkg&quot;"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by calmpey09 on 2009-05-08
how can i configure the dpkg? during my update it states that it was interrupted and i should configure the dpkg to correct it.. how can i do that?

---

### Post by Slim Odds on 2009-05-08
> **calmpey09 said:**
> how can i configure the dpkg? during my update it states that it was interrupted and i should configure the dpkg to correct it.. how can i do that?

Exactly what did it say?

dpkg is a program.

---

### Post by overdrank on 2009-05-08
> **calmpey09 said:**
> how can i configure the dpkg? during my update it states that it was interrupted and i should configure the dpkg to correct it.. how can i do that?
You may try the command ```
sudo dpkg--configure-a
```

---

### Post by calmpey09 on 2009-05-08
this is wat it says...

> 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


what will i do next?

---

### Post by sisco311 on 2009-05-08
Open a terminal (Application -> Accessories -> Terminal)
and copy/paste the command:
```
sudo dpkg --configure -a
```

---

### Post by calmpey09 on 2009-05-08
what's the next? it give me options... how can i report the problem?

---

### Post by raymondh on 2009-05-08
> **calmpey09 said:**
> what's the next? it give me options... how can i report the problem?

Calmpy .... in terminal, go ahead and

```
sudo apt-get update
```

and see if you complete an update

Oks lang yan 'pre. kaya natin 'yan :)

---

### Post by calmpey09 on 2009-05-08
thanks.... but it has an error on "BLUEZ"... its for bluetooth right? but my laptop has no bluetooth....

---

