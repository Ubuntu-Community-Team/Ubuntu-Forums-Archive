---
title: "ubuntu says i dont have permissions but im the only user!!!"
date: 2008-10-17
forum: General Help
---

### Post by reinaldistic on 2008-10-17
ok, i installed ubuntu from kbuntu which i didnt like very much, i had a username on kbuntu, but that stayed with ubuntu so im asuming im admin, now in ubuntu i tried to change system files but it wont let me it says i dont have permissions, ok so i edit permisions on system>administration>authorizations and still it doesnt work, then i notice in rght click>properties>permisiions it says that im not allowed to edit permisiions only owner can and later i find out the "owner" is "root, a username called root" so i try to log in as root, but then ubuntu tells me "administrator is not allowed to log in from this screen, so what can i do??!?!?!?!

ps i do know the password for root because it allowed me to change it in administration>users and groups

---

### Post by WWSmith36 on 2008-10-17
Users only have permission to write to one folder on the machine, their home folder.  All the other folders are protected.  If you want do have superuser permission, you must invoke a form of the sudo command.

For example, to get root access from the terminal
```
sudo -i
```

To open nautilus with root access
```
gksudo nautilus
```

This is done so that users do not mess their machine up.  Be **very carefull** when doing things way.  You can easily **ruin your system** if do not know what you are doing.

It is better you issue just a single limited scope command like
```
sudo gedit /file/to/be/edited
```

Please let me know what you are trying to do to your system, I may be able to provide more useful information.

---

### Post by reinaldistic on 2008-10-17
i am trying to change menu.lst to make it so that my default becomes win xp and my timeout is 3 sec, thats it and it wont let me do it

---

### Post by WWSmith36 on 2008-10-17
Its best to do it this way

```
gksudo gedit /boot/grub/menu.lst
```

This is allow you change your menu.lst

---

### Post by reinaldistic on 2008-10-17
thank you, i was accesing it through the terminal, but with another command... someone in this forum told me to... thanks again

---

### Post by sisco311 on 2008-10-17
> **reinaldistic said:**
> i am trying to change menu.lst to make it so that my default becomes win xp and my timeout is 3 sec, thats it and it wont let me do it

you can use startupmanager to change the default os and timeout.

install it with add/remove, synaptic or from a terminal:
```
sudo aptitude install startupmanager
```

if you want to open Startup Manager go to System&#8212;>Administration&#8212;>Startup-Manager

---

