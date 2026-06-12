---
title: "Installing aMSN skins and plugins"
date: 2008-08-20
forum: General Help
---

### Post by tumateix on 2008-08-20
Hi,

I've got a problem when installing aMSN skins and plugins. I've downloaded the archive from amsn site and i've exctracted it correctly, but I can't copy it to the following directory:

**/usr/share/amsn/skins**

I've tried to do *right click -> Propierties -> Permissions* in that folder in order to change permissions and being able to edit archives and subfolders, but the I've found this warning: ***"You are not the owner, so you can't change this permissions"***. The owner is the user **root**. How can I change this?

A screenshot [here]("http://img175.imageshack.us/img175/7991/screenshottd0.png").

I'm new on ubuntu, but I'm afraid I will have the same problem whenever I try to edit a folder in the **/usr** directory. I'd like to know how to solve that.

Thank you.

---

### Post by tumateix on 2008-08-20
Well, I do have this problem with any type of folder edition in /usr :(

---

### Post by stormtrooprdave on 2008-08-20
My amsn skins and plugins are in a hidden directory in my home folder, not in the one you mentioned

---

### Post by tumateix on 2008-08-20
I was just following the [Plugins and Skins installation guide]("http://www.amsn-project.net/wiki/Installing_Plugins_and_Skins") I found on amsn website.

How did you install them?

---

### Post by stormtrooprdave on 2008-08-20
> **tumateix said:**
> I was just following the [Plugins and Skins installation guide]("http://www.amsn-project.net/wiki/Installing_Plugins_and_Skins") I found on amsn website.

How did you install them?

I put mine in 

/home/dave/.amsn/skins  (or plugins as applicable)

They automatically show up in the skins & plugins menus next time I start the program

---

### Post by tumateix on 2008-08-20
Thanks.

Now I see the skin in the skin selection dialog, but when I apply it nothing happens (I've tried to restart aMSN). Any idea?

---

### Post by stormtrooprdave on 2008-08-20
> **tumateix said:**
> Thanks.

Now I see the skin in the skin selection dialog, but when I apply it nothing happens (I've tried to restart aMSN). Any idea?

Don't know sorry, it all worked first time for me.  Maybe redownload the skin, or try some other skins to rule out a problem with that particular skin?  You might've looked already but see if there's anything on the amsn forum

[http://www.amsn-project.net/forums/]("http://www.amsn-project.net/forums/")

---

### Post by r.e.lietz on 2008-10-20
Hey, just wondering if you solved that skins problem.  I got them copied to the right folder, but can't select them.  Not sure why...

---

### Post by jordey24 on 2008-10-21
--
Sorry,i didnt read the last posts...
I'll try to search for an awnser however,i used aMSN before.

---

### Post by marin123 on 2009-12-24
sudo nautilus /usr/share/amsn/skins

it will open this location as root and you can put in whatever you want...

---

