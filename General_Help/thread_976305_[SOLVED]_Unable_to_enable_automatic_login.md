---
title: "[SOLVED] Unable to enable automatic login"
date: 2008-11-09
forum: General Help
---

### Post by gerryg on 2008-11-09
Hi everybody,

I'm having problems with getting an automatic login to work. In the
"Login Window Preferences", I checked "Enable Automatic Login",
selected a user and closed the window. However, this settings are not
remembered - the next time I open "Login Window Preferences", they are
lost.

Does anybody have an idea what I am doing wrong or what additional
measures I have to take in order to enable automatic login?

Many thanks,
Gerald

---

### Post by eternalnewbee on 2008-11-09
**Main Menu > System > Preferences > Sessions Preferences > Options**: Click **Remember currently running Applications**.
No guarantees if this will help, as I did like you did, but it worked for me.

---

### Post by gerryg on 2008-11-09
> **eternalnewbee said:**
> **Main Menu > System > Preferences > Sessions Preferences > Options**: Click **Remember currently running Applications**.
No guarantees if this will help, as I did like you did, but it worked for me.

I tried to follow your instructions, but it didn't have any effect on the automatic login.

Did you try any other approaches than this one?

Thx!

---

### Post by jerrylamos on 2008-11-09
Probably no help to you this time, but on install there is an option for automatic login.  I use it.  I think it is on the menu where your login and password are entered?

Jerry

---

### Post by gerryg on 2008-11-09
> **jerrylamos said:**
> Probably no help to you this time, but on install there is an option for automatic login.  I use it.  I think it is on the menu where your login and password are entered?

I'm afraid you were right in that this didn't really help.
In the login menu, there are not many options, at least not for automatic login.

Do I have to (re)install a particular package?

Thx,
Gerald

---

### Post by gerryg on 2009-01-10
Hi all,

I just found the thread ["GDM Login Manager Preferences wont save"]("http://ubuntuforums.org/showthread.php?t=907590"), where a method to solve my problem is described:

I had a file /etc/gdm/gdm.conf-custom of size 0. Here is what I did:
```
cd /etc/gdm
rm gdm.conf-custom
cp gdm.conf gdm.conf-custom
```

After that, the preferences could be saved...

Regards,
Gerald

---

