---
title: "Permission to save file"
date: 2008-07-15
forum: General Help
---

### Post by whalogreg on 2008-07-15
I want to edit my "xorg.conf" but when I try to save I get the error 

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

How can I do this? Should I try doing this in gedit or some other app?

---

### Post by sisco311 on 2008-07-15
Edit the file as root:
Open a terminal.
Backup the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Edit it:
```
gksu gedit /etc/X11/xorg.conf
```


If you want to restore the original:
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

---

### Post by whalogreg on 2008-07-15
> **sisco311 said:**
> Edit the file as root:
Open a terminal.
Backup the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Edit it:
```
gksu gedit /etc/X11/xorg.conf
```


If you want to restore the original:
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

Thanks! It's been a few months since I've used linux... (I'm prob gonna be one of those guys who knows just enough to screw everything up, but not enough to fix it... ha)

---

### Post by issih on 2008-07-15
Ok, the advice you got above is bang on, here is why:

Every file in ubuntu maintains three sets of parameters that specify what different users can do with the file.

All these sets consist of three values, stating whether a particular type of user can:
1) read the file
2) write to the file
3) execute (run) the file

The first set of rights relate to the rights of files owner (usually the creator of the file), and specify whether he/she can read/write/execute the file

The second set relate to and groups the owner belong to

The final set relate to all other users of the system.

In this way files are protected from being manipulated by unauthorised users.

The system uses this permissions system to protect files that are an important part of the operating system, to stop casual users from damaging the smooth running of the system.

In order to be able to sidestep this permissions system you have to run as the root user (who is basically god, and can do anything he pleases).

In ubuntu, rather than directly logging in as the root user, it is possible (provided your user belongs to the admin group, which it will by default) to temporarily impersonate the root user.

This is achieved with the sudo or gksudo (for graphical apps) commands.

Sudo stands for Super User do, and effectively instructs the system to run the following comand as the root user. In order to ensure that you really mean to do this, the system requires you to enter your login password.

So by editing the file with "gksudo gedit" you basically open a text editor running with root privileges which can then save the file to the protected location.

Hope that helps

---

