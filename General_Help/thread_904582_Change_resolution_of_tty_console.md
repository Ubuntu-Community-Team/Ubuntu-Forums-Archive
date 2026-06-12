---
title: "Change resolution of tty console"
date: 2008-08-29
forum: General Help
---

### Post by deelazy on 2008-08-29
Hi,

I trying to change tty the resolution of tty console without changing option of /boot/grub/menu.lst . Why ? becaus I use nvidia beta drivers and when I change vga resolution in menu.lst it make graphic bugs.

I search in /etc/default/console-setup but i don't know options ...

Plz give me some help =].

---

### Post by deelazy on 2008-09-04
woaw

---

### Post by eldragon on 2008-09-04
```

$ sudo apt-get install startupmanager

```
then run it with
```

$ sudo startupmanager

```

you will find the setting there.

---

### Post by deelazy on 2008-09-04
I will try thanks a lot.

---

