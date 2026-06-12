---
title: "Installed Hidpoint but it is locked and unusable!"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by Ozdemon on 2009-05-23
I downloaded the latest Hidpoint release which at last is 64bit compatible.  It is a bin file.  I followed the instructions at post #10 [http://ubuntuforums.org/showthread.php?t=372716]("http://ubuntuforums.org/showthread.php?t=372716") here and it seemed to install okay.

Now I have 2 icons on my desktop, hidpoint and remove hidpoint. Both are locked.  I have rightclicked to change permissions, but that option is greyed out.  The owner is shown as root.  I went to the application directory at /opt/hidpoint using gksudo nautilus and tried to change permissions there.  I did, but it made no difference.

So after waiting many months for this application, I have installed it.  I just can't use it.   ](*,)

I don't know what else to do to change permissions to allow me and another user to use the program.

Help really appreciated.

---

### Post by labinnsw on 2009-05-23
In a terminal (Applications >> Accessories >> Terminal) Type:

```
sudo nautilus
```

Supply your password.

This will give you administrative access. Now you can change the permissions. Just remember to close this GUI when you are finished so you don't keep working as a super user.

---

### Post by Ozdemon on 2009-05-23
> **labinnsw said:**
> In a terminal (Applications >> Accessories >> Terminal) Type:

```
sudo nautilus
```

Supply your password.

This will give you administrative access. Now you can change the permissions. Just remember to close this GUI when you are finished so you don't keep working as a super user.

Thanks, that worked :D

Now I can get my keyboard fully functional!  ):P

---

