---
title: "root Help"
date: 2008-07-30
forum: General Help
---

### Post by lupinesoul on 2008-07-30
I don't have an account named root.  I have only one account on my computer that is recognized as the Administrator.  I can't edit the files in this folder, but I really want to.

Have you played Egoboo?  It's not so easy without a numpad...

---

### Post by caljohnsmith on 2008-07-30
Ubuntu does not have the root account enabled by default for security reasons. If you need to run anything as root, you just need to put a "sudo" in front of it, or "gksudo" if it is a graphical program, and enter your own password.

---

### Post by Ataris on 2008-07-30
As for the game, I assume this is a rabbit trail....

There is no account called root. To use root functions and do admin commands you must open the terminal and use the command sudo or gksudo + what program or file browser you want to use.

Read this [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by lupinesoul on 2008-07-30
> **caljohnsmith said:**
> Ubuntu does not have the root account enabled by default for security reasons. If you need to run anything as root, you just need to put a "sudo" in front of it, or "gksudo" if it is a graphical program, and enter your own password.

Okay, I don't have the greatest idea of how to go about this.  It's located in "/etc/egoboo" and I'm trying to edit and save "controls.txt", so I started with

```
cd /etc/egoboo
sudo controls.txt
```

I don't think there's anything wrong with the first line (it's just getting there), but there has to be something wrong with the second line.

---

### Post by sisco311 on 2008-07-30
the default file editor is gedit:
```
gksu gedit /etc/egoboo/controls.txt
```

---

### Post by lupinesoul on 2008-07-30
> **Ataris said:**
> As for the game, I assume this is a rabbit trail....

There is no account called root. To use root functions and do admin commands you must open the terminal and use the command sudo or gksudo + what program or file browser you want to use.

Read this [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Thanks!  That helped a lot.

---

### Post by Ataris on 2008-07-30
Try ```
sudo gedit controls.txt
``` You have to tell the terminal what program to use after the sudo. And don't be worried if the password is invisible when it asks you to type it in.

---

### Post by bodhi.zazen on 2008-07-30
> **Ataris said:**
> As for the game, I assume this is a rabbit trail....

There is no account called root. To use root functions and do admin commands you must open the terminal and use the command sudo or gksudo + what program or file browser you want to use.

Read this [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Nice post :)

There is a root account, by default it is locked.

Root's home directory is /root and you can become root with

```
sudo -i
```

or 

```
sudo su
```

or boot to recovery mode, select root command line.

---

### Post by sisco311 on 2008-07-30
> **Ataris said:**
> Try ```
sudo gedit controls.txt
``` You have to tell the terminal what program to use after the sudo. And don't be worried if the password is invisible when it asks you to type it in.
and of course gedit is a GUI application :)
```
gksu gedit *filename*
```or
```
gksudo gedit *filename*
```

---

