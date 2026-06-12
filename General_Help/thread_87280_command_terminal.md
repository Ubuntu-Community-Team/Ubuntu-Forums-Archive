---
title: "command terminal"
date: 2005-11-07
forum: General Help
---

### Post by ivanp on 2005-11-07
Hi, I've just swap from FC3 to ubuntu and I must say is great. I'm just needing two things: during installation I was never asked for the **root password**, so I don't know it; and second, I guess there is a **bash for graphic mode**, but can't find it. Thnaks in advance,

Ivan

---

### Post by Kyral on 2005-11-07
Root is disabled by default. You enter Root by using

```
sudo command
```

The password is your user password. All the GUI config apps have been patched to use sudo as well.

As for "Bash for Graphic Mode", I've never heard of it

---

### Post by az on 2005-11-07
Accessories - Terminal

Gnome terminal.

---

### Post by 23meg on 2005-11-07
If you do need to use the root account, you can create a pass for it by typing ```
sudo passwd root
```Sudo is a better practice though; stick to it.

---

### Post by endersshadow on 2005-11-07
It's important to note that by default, Ubuntu will not let you log in as root from the GDM login screen, a major change from Fedora.  You can, as in Fedora, use:

```
su root
```

Just some FYI coming from one FC3 user to another :)

---

### Post by ivanp on 2005-11-08
Thanks a lot!
just one question: is sudo executing commands as the root user because is in its group? does sudo have all the privilegies that root has?

---

### Post by Kyral on 2005-11-08
If you know how to use su (and it seems like you do) then you can think of sudo as being an alias to "su -c"

Works the same way

If you don't know how su works, then just think of it this way, sudo just runs the command as root. (SuperUserDO if you will). It isn't its own user

---

### Post by ivanp on 2005-11-08
Thanks a lot again!
I'm glad I found Ubuntu.

---

