---
title: "prevent a user from accessing the CDROM drive"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2009-05-09
I have only ssh access to a remote Ubuntu 8.04.2 system.
I can sudo.
There are 5 user accounts on this system.
All 5 users have access to the all the devices on this system.
Now I need to prevent 2 users from using the CDROM drive.
Which files do I edit to apply these restrictions (via ssh)?

---

### Post by ibuclaw on 2009-05-09
Go into: **System->Administration->Users and Groups**

Click on "**Unlock**", and enter in your password.

Then select the user that you want to deny CDROM drive access and click "**Properties**".
Under the "**User Privileges**" tab, uncheck "**Use CD-ROM devices**"

Regards
Iain

---

### Post by boondocks on 2009-05-09
> **tinivole said:**
> Go into: **System->Administration->Users and Groups**

Click on "**Unlock**", and enter in your password.

Then select the user that you want to deny CDROM drive access and click "**Properties**".
Under the "**User Privileges**" tab, uncheck "**Use CD-ROM devices**"

Regards
Iain

Yes, I can do this from the desktop.
But I do not have access to the desktop.
I have only ssh access to this remote Ubuntu 8.04.2 system.
I can sudo.

---

### Post by cariboo on 2009-05-09
You can use usermod to remove the groups you want. Instead of removing the group, you have to modify which groups the user is in. For example for my user, I am in the following groups:

```
jim adm dialout cdrom plugdev lpadmin admin sambashare
```

If I wanted to remove the cdrom group I would enter the following command

```
usermod -G adm,dialout,plugdev,lpadmin,admin,sambashare jim
```

---

### Post by ibuclaw on 2009-05-09
> **boondocks said:**
> Yes, I can do this from the desktop.
But I do not have access to the desktop.
I have only ssh access to this remote Ubuntu 8.04.2 system.
I can sudo.
ssh is X transparent too, you know, run:
```
ssh -X **192.168.1.1** users-admin
```
Except replace 192.168.1.1 with the IP address of the server.

Regards
Iain

---

### Post by boondocks on 2009-05-09
> **tinivole said:**
> ssh is X transparent too, you know, run:
```
ssh -X **192.168.1.1** users-admin
```
Except replace 192.168.1.1 with the IP address of the server.

Regards
Iain

Ok.  I tried:
> ssh  -X  192.168.3.9  users-admin
```
boondocks@192.168.3.9's password:
/usr/bin/X11/xauth:  /home/boondocks/.Xauthority not writable, changes will be ignored
X11 connection rejected because of wrong authentication.

(users-admin:7329): Gtk-WARNING **: cannot open display: localhost:10.0
```

---

### Post by boondocks on 2009-05-09
Ok.  So I changed the permissions on "/home/boondocks/.Xauthority" and now it is writable.

Yes, it does display the "Users Settings" window.
Now I can see the 5 user accounts on that remote system.

But these accounts are all grayed out.
Even the "Unlock" button is grayed out.
I selected a User and still the "Unlock" button is grayed out.

---

