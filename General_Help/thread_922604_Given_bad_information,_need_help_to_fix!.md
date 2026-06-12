---
title: "Given bad information, need help to fix!"
date: 2008-09-17
forum: General Help
---

### Post by epic1990 on 2008-09-17
I am new to linux, so I was needing some help. I know what I need to change in the /etc/network/interfaces, however I cannot seem to save it; has been a while since I screwed this up.

<!--auto--> lo
<!--iface--> lo <!--inet loopback
-->
I need to remove the comments, but I cannot seem to take the program out of readonly. Please help.

---

### Post by Elfy on 2008-09-17
You need to be root to do it - sudo for terminal commands, gksudo for gui apps.

To edit the file with gedit you would need to 

```
gksudo gedit /etc/network/interfaces
```

---

### Post by northern lights on 2008-09-17
```
gksu gedit /etc/network/interfaces
```or```
sudo nano /etc/network/interfaces
```would give you access

---

### Post by northern lights on 2008-09-17
[QUOTE=epic1990]Thank you very much for your help. If it isn't too much trouble, what is the difference between gksu, and sudo nano?[/QUOTE]
gedit is a GUI text-editor while nano will open within the shell.

P.S. Rather than PMing, please keep support requests in the forums themselves. Thank you.

---

