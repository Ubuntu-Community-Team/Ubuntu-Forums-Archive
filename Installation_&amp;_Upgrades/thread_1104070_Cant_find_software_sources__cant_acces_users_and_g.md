---
title: "Cant find software sources \ cant acces users and groups"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by Rany Albeg on 2009-03-23
Hi guys ,

1) I cant find System->Administration->software sources.

2) I cant acces System->Administration-> Users and groups.
   I get the error: "The configuration could not be loaded.
   you are not allowed to access the system configuration"


Thanks for helping.

---

### Post by oldrocker99 on 2009-03-23
You certainly should be able to find them; try a fresh installation.

:guitar:

---

### Post by oldos2er on 2009-03-23
> **Rany Albeg said:**
> Hi guys ,

1) I cant find System->Administration->software sources.

2) I cant acces System->Administration-> Users and groups.
   I get the error: "The configuration could not be loaded.
   you are not allowed to access the system configuration"
  

 Check System, Preferences, Main Menu to see if Software Sources has been disabled. If that doesn't work, you can create a launcher for it using this as command: ```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```
 You are running Gnome, correct?

---

### Post by hyper_ch on 2009-03-23
or you could use my generator in my sig to generate the sources.list

---

### Post by Rany Albeg on 2009-03-23
Yes i do work with GNOME.

Well i saw im "Main Menu" that "softwar sources" is disabled.
I tried to enable "software sources" but when i checked the box
the V sign disappears.
Do i need a special permission for that?

Also what about the access to "Users and Groups" , do you have any idea?

Thank you.

---

### Post by oldos2er on 2009-03-23
Check Main Menus settings again, and make sure Administration (under System) is checked. That would explain why both Software Sources and Users & Groups are missing.

---

### Post by Rany Albeg on 2009-03-25
I cant understand what you mean.
i go System->Administration->Main Menu

and Administration is a category , i cant check it.
can u explain again in details? im a beginner so its quite hard.

Thank you all for helping.

---

### Post by rjl6591 on 2009-03-25
It looks as though you are trying to do things that require 'administrator' privileges from a user account that doesn't have them.

You can only change this from an account that does have admin privileges. (It's a basic security feature to stop unauthorised users from meddling with the machine.)

Go to System -> Administration -> Users and Groups.
Click on 'Unlock' and enter password.
Then select the username you wish to give admin privileges to, then click on Properties, then select User Privileges tab, then tick the boxes you want, then click on OK to save.

---

### Post by Rany Albeg on 2009-03-26
Thanks , but i mentioned before that when i try to go Users and Groups i get an error "The configuration could not be loaded. You are not allowed to access the system configuration"

Must be a way to edit some file under su , am i right?

---

### Post by rjl6591 on 2009-03-27
> **Rany Albeg said:**
> Thanks , but i mentioned before that when i try to go Users and Groups i get an error "The configuration could not be loaded. You are not allowed to access the system configuration"

Must be a way to edit some file under su , am i right?

You can check to make sure you're a member of the admin group:

```
grep ^admin /etc/group
```

This should produce a line something like this, with the authorised sudoers listed:

```
admin:x:115:rany
```

If you want to give a user admin rights, type:

```
sudo adduser <username> admin
```

---

### Post by HydroTech on 2009-03-28
Hey, I have almost the same problem. I can access software sources but I don't have permission to open "users and groups." instead I get an error saying:
 "The configuration could not be loaded.
  You are not allowed to access the system configuration."
I used to have almost full read/write access to everything but I changed a few things(not sure what though-LOL) and now I don't have admin rights to anything.

my linux version = Ubuntu 8.10 Ibex

---

### Post by Rany Albeg on 2009-03-31
Thank you all , i used rjl6591's advice. worked for me.

---

### Post by jpmneofito@gmail.com on 2009-04-07
Hi,

I have the same problem. When I added my user to another group using the command
```
$ sudo usermod -G vboxusers jp
```
something goes wrong and after that I could not access "users and group menu".

Then I added my user to sudoers file (you can use *sudo adduser <username> admin*) and added my user to "admin" group again:
```
$ sudo usermod -G admin jp
```

Now everything is OK.

:D

---

### Post by jpmneofito@gmail.com on 2009-04-07
Hi,

I found my error, it was when executing the command:
```
$ sudo usermod -G vboxusers jp
```
The command above removes the user "jp" from ALL groups and adds it to "vboxusers" group. The correct is add the option "-a", which causes the user to be "appended" to the group specified:
```
usermod -a -G vboxusers jp
```

It's my fault...  :'(

---

