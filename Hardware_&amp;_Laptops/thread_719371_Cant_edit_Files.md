---
title: "Cant edit Files?"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by Nitro Fan on 2008-03-09
i am trying to edit a file  but when I try to save the file xorg.conf I get the following error message


[COLOR="Red"]Could not save the file /etc/X11/xorg.conf.
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.[/COLOR]

do I need to be in administrator or something? if so how do I do that!? (I am a total newbie to all this and struggling badly!!)


I have tried typing gksudo gedit but it does not ask me for my password and when gedit opens I cannot see any files other than those in my home dir!

Thanks Guys

---

### Post by lloyd_b on 2008-03-09
> **Nitro Fan said:**
> i am trying to edit a file  but when I try to save the file xorg.conf I get the following error message


[COLOR="Red"]Could not save the file /etc/X11/xorg.conf.
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.[/COLOR]

do I need to be in administrator or something? if so how do I do that!? (I am a total newbie to all this and struggling badly!!)


I have tried typing gksudo gedit but it does not ask me for my password and when gedit opens I cannot see any files other than those in my home dir!

Thanks Guys

Yes, you *do* need root permissions to change that particular file.

Try "gksudo gedit /etc/X11/xorg.conf".  There's probably a way to navigate to that file within gedit, but I haven't used that editor so I can't tell you what it is...

And note that sudo/gksudo will not always ask for your password - there's a "grace period" after using them once before your password is required again (15 minutes, IIRC).

Lloyd B.

---

### Post by Kevbert on 2008-03-09
Try using 
sudo gedit /etc/X11/xorg.conf from Terminal.

---

### Post by banewman on 2008-03-09
Open system - admin - users and groups
from the menu and make sure your user has admin group access
:)

---

### Post by Nitro Fan on 2008-03-09
> **Kevbert said:**
> Try using 
sudo gedit /etc/X11/xorg.conf from Terminal.

That is exactly what I have been doing!

---

### Post by Nitro Fan on 2008-03-09
> **banewman said:**
> Open system - admin - users and groups
from the menu and make sure your user has admin group access
:)

yep got admin group access!

---

### Post by Yellow Pasque on 2008-03-09
Are you still having probs? Let's try this to see permissions:
```
cd /etc/X11
ls -l | grep xorg
```

You can then try changing the permissions if they're fuxored:
```
sudo chmod 775 xorg.conf
```

---

### Post by Nitro Fan on 2008-03-10
Hi Temüjin
I am stull having probs but have been away for a cpouple of days so i will try this tonight, what does Fuxored mean please?

---

### Post by sfink16 on 2008-03-11
Try sudo -s first.  It will ask for your root admin password.  Then do your sudo gedit.  Worked for me!

Steve
> **Nitro Fan said:**
> That is exactly what I have been doing!

---

