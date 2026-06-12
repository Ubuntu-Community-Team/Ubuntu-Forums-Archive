---
title: "I am not the owner and I do not have permissions...HUH!?!"
date: 2008-07-11
forum: General Help
---

### Post by sirbingo on 2008-07-11
I'm trying to install skins into Audacious by copying the skins I've downloaded into the Audacious skins folder (/usr/share/audacious/Skins)

so far so good... but UBUNTU is saying I am not the owner and I do not have permissions to copy stuff into this folder?  Huh?!? :confused: 

How come I am not the owner.  I installed this program and I could have sworn I set myself up as the "Admin" or what ever it is called in UBUNTU?!?!

AARGH!!!   :o

---

### Post by chris4585 on 2008-07-11
what is your user account?

run

```
gksudo nautilus 
```

go to the audiacious skin folder, right click > properties > permissions 

make sure your user name or account you use is the same, if not then change it in that dialog

---

### Post by Zack McCool on 2008-07-11
You are not the owner.  You are a user.  Your account is part of the admin group, so you have sudo rights.  You just have to do things a little differently.  

If you are comfortable at the command line, you can copy with the following:  (When it asks for a password, just enter your user password)

```
 sudo cp /source/files /usr/share/audacious/Skins 
```

If you prefer a gui, open a terminal anyhow, but type:

```
 sudo nautilus 
```

And do the copy from there.

This is different from Windows.  In Linux, system files are protected by ownership.  A user does not have ready write access to everything on the system.  This is what makes Linux so much more stable and protected from malware.  It also makes things slightly less convenient, but you get used to that and it becomes second nature.

---

### Post by aysiu on 2008-07-12
*gksudo nautilus*, not *sudo nautilus*.

Probably won't have too many bad ramifications for Nautilus, but it's a good habit to get into to use *gksudo* for graphical applications. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by fahadsadah on 2008-07-12
> **aysiu said:**
> *gksudo nautilus*, not *sudo nautilus*.

****Probably won't have too many bad ramifications for Nautilus****, but it's a good habit to get into to use *gksudo* for graphical applications. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I screwed up my whole system by using sudo nautilus.

It messes up loads of permissions.

---

