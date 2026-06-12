---
title: "Synaptic Package Manager problem"
date: 2008-07-22
forum: General Help
---

### Post by jkyahoo101 on 2008-07-22
When I start the package manager to install something I get this.

Starting without administrative privileges

You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them.

I can't reload or apply any new packages. How do I fix this?

---

### Post by Potatoj316 on 2008-07-22
Your starting synaptic right, not the add/remove programs thing?  You could use aptitude in the terminal.  Just type aptitude and you will have a synaptic-like interface.  Or aptitude search SEARCHTERM then aptitude install PACKAGE

---

### Post by PaxAmericana on 2008-07-22
Just open Synaptic from command line as super user.

yourname@yourmachinesname:~$ sudo synaptic


This will give you privileges and open synaptic in a new window.

---

### Post by avtolle on 2008-07-22
By chance, did you create another user for your computer which user has no administrative privileges? If you did, then you would need to add this user to the admin group under System>>Administration>>Users and Groups.

---

### Post by jkyahoo101 on 2008-07-22
No I don't have any other users besides me and I have admin privileges. I did sudo synaptic and it worked for me. I guess I will just have to access it that way. Thanks for the help.

---

### Post by Tim Sharitt on 2008-07-22
Goto edit menus and make sure the launcher command for synaptic is 'gksu /usr/sbin/synaptic'. If it is there may be a problem with gksu, hit Alt-F2 
andn enter
```
gksu /usr/sbin/synaptic
```

---

### Post by PaxAmericana on 2008-07-22
Glad I could help. That's the only way I access synaptic. Terminal's history makes it painless though, that and the program yakuake from the repositories. It allows the whole upgrade/update/install process to happen in two keystrokes plus your password.

---

### Post by bodhi.zazen on 2008-07-22
> **PaxAmericana said:**
> Just open Synaptic from command line as super user.

yourname@yourmachinesname:~$ sudo synaptic


This will give you privileges and open synaptic in a new window.

> **PaxAmericana said:**
> Glad I could help. That's the only way I access synaptic. Terminal's history makes it painless though, that and the program yakuake from the repositories. It allows the whole upgrade/update/install process to happen in two keystrokes plus your password.

Please use gksu for running graphical applications. gksu give "sane" , safe root access to X applications.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Also the "fix" it either to fix your menu as suggested by Tim Sharitt or, if that fails, fix gksu :lolflag:

---

