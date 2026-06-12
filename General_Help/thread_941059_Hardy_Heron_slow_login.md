---
title: "Hardy Heron: slow login"
date: 2008-10-07
forum: General Help
---

### Post by gaijindewanai on 2008-10-07
i've been using Hardy Heron since its release.
It run flawlessly back then, it only takes 20 minutes to login (from login screen to the desktop), but now it become slow... it takes 40 minutes!!!

there is no unusual thing in my session (preference) and my service (administration).

i thought that gnome has become fatter, is that true?
however, i minimize the compiz but, still, no significant change.

Do anyone know how to help me? i want my computer' speed back.
or do i need to wait for intrepid ibex to solve it?
i heard that ibex is gonna be much faster <-------i'm not sure bout this part, just rumor.

---

### Post by arsham on 2008-10-07
20 minutes?
wow!

ok, is it connected to internet?
Do this command in a terminal and see if there are any lines start with 127.0.0.1?

```
cat /etc/hosts

```

I had the same problem (not for 20 minutes, but almost 3-4 minutes strange halt on the X server) and I solved it by adding a :
```

127.0.0.1 lo
```

in my /etc/hosts file



> **gaijindewanai said:**
> i've been using Hardy Heron since its release.
It run flawlessly back then, it only takes 20 minutes to login (from login screen to the desktop), but now it become slow... it takes 40 minutes!!!

there is no unusual thing in my session (preference) and my service (administration).

i thought that gnome has become fatter, is that true?
however, i minimize the compiz but, still, no significant change.

Do anyone know how to help me? i want my computer' speed back.
or do i need to wait for intrepid ibex to solve it?
i heard that ibex is gonna be much faster <-------i'm not sure bout this part, just rumor.

---

### Post by lovinglinux on 2008-10-07
> **gaijindewanai said:**
> i've been using Hardy Heron since its release.
It run flawlessly back then, it only takes 20 minutes to login (from login screen to the desktop), but now it become slow... it takes 40 minutes!!!

Do you think 20 minutes is not slow but 40 minutes is? Did you typed minutes instead of seconds by mistake?

---

### Post by gaijindewanai on 2008-10-07
wooopss!!

sorry, i rushed.. n made a silly mistake..
should be SECONDS not minutes...

so, what should i do?
i want the 20 seconds back..

---

### Post by lovinglinux on 2008-10-08
> **gaijindewanai said:**
> wooopss!!

sorry, i rushed.. n made a silly mistake..
should be SECONDS not minutes...

so, what should i do?
i want the 20 seconds back..

I don't know if this will help, but Instead of using the session manager to automatically launch several applications I use regularly (Tomboy, Specto, Easystroke, Cairo, Conky...) I have a script in which I create a delay to each application start, so I get the desktop running faster and the applications are launched anyway, but not all at the same time.

---

### Post by gaijindewanai on 2008-10-08
well..

I have no application running except Compiz (i dont use the cube thingy) and Gnome (with 2 default panels).
no tomboy, no conky, no awn, no cairo, nothing else.

I,m confused...... :confused:

---

