---
title: "HELP me cant delete folder!!!"
date: 2008-08-06
forum: General Help
---

### Post by peepymouse on 2008-08-06
OK i downloaded java and untar'd it and now i cant delete it it says im not the owner but i am the only user on the computer please help
and i realy want to get rid of that folder thats standing on the middle of my desktop (java)

---

### Post by mdsharp24 on 2008-08-06
gksudo nautilus /home/your-username/Desktop

right click, remove file

---

### Post by mikjp on 2008-08-06
sudo rmdir

---

### Post by roachk71 on 2008-08-06
You could try performing the deletion as root , using:
```
sudo nautilus
```
and retrying the delete operation, or installing Midnight Commander (mc) through synaptic, and using sudo to run that in a terminal.

---

### Post by ilrudie on 2008-08-06
> **roachk71 said:**
> You could try performing the deletion as root , using:
```
sudo nautilus
```and retrying the delete operation, or installing Midnight Commander (mc) through synaptic, and using sudo to run that in a terminal.

Don't use sudo to run nautilus or any other graphical application.  Always use gksudo when dealing with graphical applications.

gksudo nautilus will let you delete the folder (and any other folder/file on your system so be careful when you are using gksudo)

---

### Post by peepymouse on 2008-08-06
thankx guys i hope it will work

(and ty for fast response :)

---

### Post by peepymouse on 2008-08-06
> **mdsharp24 said:**
> gksudo nautilus /home/your-username/Desktop

right click, remove file

This worked TY !!! i will not forget it it

---

### Post by roachk71 on 2008-08-06
> **ilrudie said:**
> Don't use sudo to run nautilus or any other graphical application.  Always use gksudo when dealing with graphical applications.

gksudo nautilus will let you delete the folder (and any other folder/file on your system so be careful when you are using gksudo)

Thanks for reminding me. I'm so used to using the terminal, that I'd kinda forgotten about the built-in Run dialog (which I often use, btw)... :KS

---

