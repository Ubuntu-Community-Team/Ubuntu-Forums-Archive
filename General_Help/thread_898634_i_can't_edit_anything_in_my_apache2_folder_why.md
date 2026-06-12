---
title: "i can't edit anything in my apache2 folder why?"
date: 2008-08-23
forum: General Help
---

### Post by dxlwebs on 2008-08-23
Hey all,

i would like to change some stuff in my apache2.conf file and in sites available area and things but i don't seem to have permission i can even copy anything or add anything does anyone know why and how to fix

thnx for your help

---

### Post by LateNiteTV on 2008-08-23
> **dxlwebs said:**
> Hey all,

i would like to change some stuff in my apache2.conf file and in sites available area and things but **i don't seem to have permission** i can even copy anything or add anything does anyone know why and how to fix

thnx for your help

that answers your question right there. you need to "su" to the owner of the files to edit them.

---

### Post by Joeb454 on 2008-08-23
Try ```
gksudo gedit /path/to/apache2.conf
```

---

### Post by dxlwebs on 2008-08-23
> **LateNiteTV said:**
> that answers your question right there. you need to "su" to the owner of the files to edit them.

not sure i understand what you mean 

i am a root user so i should be able to change anything i want as its my own server i built it around a week or two ago!

and to the second post will that make it so that i can edit the files ? as i am using desktop and not the server version

---

### Post by mbeach on 2008-08-23
You might want to take a read of:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You are probably not user 'root'.

---

### Post by dxlwebs on 2008-08-24
well in the users and groupes section in the administrator area it says under my username that i am in group root

---

### Post by dexter.deepak on 2008-08-24
you must have a read here :
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
you are actually facing problems because you have to "act as a root"(using sudo) everytime you have to access those apache files.

---

