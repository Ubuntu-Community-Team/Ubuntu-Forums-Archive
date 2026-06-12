---
title: "i have some problem (please read)"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by royaflash on 2009-08-26
hellow 
i have problem i can not run add/remove (gnome-app-inistall er)(run and show in the bottom panel and not able to run )

when i want shutdown computer or restart ... want password and idont want type password (before not want)
dont use wifi (dont show wifi option )(before can use wifi )
thanks 
successfully and be linux

---

### Post by running_rabbit07 on 2009-08-26
I can help you with the Login wanting sign in and password.

Go to System>Administration>Login Window. Go to the Security tab and check the box for Enable Automatic Login and select your screen name.

If you need more help with this, let me know. 

As for the WIFI, I don't use it, so I don't know how to change those settings.

---

### Post by doas777 on 2009-08-26
what happens when you try to open Applications -> Add Remove? is there an error? or is it just because you don't have a network connection?

if you open a terminal (Applications -> Accessories -> Terminal) and enter:
```

sudo lshw -C network

```
what is the output?

---

