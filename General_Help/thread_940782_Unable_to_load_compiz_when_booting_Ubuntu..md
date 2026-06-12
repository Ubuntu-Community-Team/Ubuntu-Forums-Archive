---
title: "Unable to load compiz when booting Ubuntu."
date: 2008-10-07
forum: General Help
---

### Post by SandyM on 2008-10-07
I am relatively new to Ubuntu and using compiz to enhance desktop effects. Recently due to some problems I had to reinstall ubuntu. But now a new problem has arised.
Ubuntu does not auto reload compiz after I boot it as it used to be in my prior installations. 
Every time I manually reload the effects through compiz fusion icon.
**_PLEASE HELP_**

---

### Post by overdrank on 2008-10-07
> **SandyM said:**
> I am relatively new to Ubuntu and using compiz to enhance desktop effects. Recently due to some problems I had to reinstall ubuntu. But now a new problem has arised.
Ubuntu does not auto reload compiz after I boot it as it used to be in my prior installations. 
Every time I manually reload the effects through compiz fusion icon.
**_PLEASE HELP_**

Hi and have you added compiz to you sessions, located under system, preference. And add it with the command ```
compiz --replace
```


Moved :)

---

### Post by meho_r on 2008-10-07
I don't know if this would help, but I'll share some notes:

1. With my old Ati Radeon X1650 Pro graphic card it worked well with drivers installed through "Hardware drivers" interface. With drivers installed through Envy I had to reload/refresh every time after boot.

2. With nVidia 8600GT I had to reload/refresh every time no matter of driver installation method. I couldn't enable effects through "Appearance" too.

3. Try this: after installing compiz (don't omit "compiz" in Synaptic) and Fusion Icon try log on/off two-three times to see if it's ok. If not, try disabling effects in "Appearance" and then enabling them again. Try log off/on again. If OK, you can go and setup compiz preferences as liked.

---

### Post by SandyM on 2008-10-07
Thanks again sir(overdrank),it worked. And Thank u meho_r for ur reply.

---

