---
title: "[SOLVED] BOINC Getting in the way"
date: 2008-09-12
forum: General Help
---

### Post by verbal.kint on 2008-09-12
does anyone know any clever ways of getting BOINC to run in the background or out of my way somehow. 

I have it set up the way i want with regards running when the pc is idle and stuff and i just dont want it to be one of the windows on my bottom panel is there a way to make it run in the system tray or just the app to run without the GUI?

Its BOINC 6.2 and i'm running ubuntu 7.1

---

### Post by arp87 on 2008-09-13
Trying using Alltray

```
sudo apt-get install alltray

```

and then from a terminal, or a launcher (or even better, as a startup program under Sessions):

```
alltray --skip-taskbar boincmgr
```

---

### Post by verbal.kint on 2008-09-13
excellent, i love it!! thanks

---

