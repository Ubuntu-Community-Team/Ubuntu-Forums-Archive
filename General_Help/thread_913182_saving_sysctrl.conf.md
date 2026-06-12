---
title: "saving sysctrl.conf"
date: 2008-09-07
forum: General Help
---

### Post by tintumat on 2008-09-07
while i was saving a sysctrl.conf file yes day it said that i didnt have the ownership rights though i was the admin

---

### Post by sdennie on 2008-09-07
Being admin mostly just grants you the right to use the sudo command.  Try either:

```

sudo nano /etc/sysctl.conf

```

or

```

gksudo gedit /etc/sysctl.conf

```

---

### Post by tintumat on 2008-09-08
1 stupid question where do i need to type the command(sudo nano /etc/sysctl.conf), new to ubuntu

---

### Post by Jere_ on 2008-09-08
Type the command in terminal (Applications -> Accessories -> Terminal). But I'd recommend you to use gksudo gedit / etc/sysctl.conf instead, its easier.

---

