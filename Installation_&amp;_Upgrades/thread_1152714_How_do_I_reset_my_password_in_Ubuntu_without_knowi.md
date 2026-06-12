---
title: "How do I reset my password in Ubuntu without knowing it?"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by NS RAO on 2009-05-08
**How do I reset my password in Ubuntu without knowing it?**

I recently installed Ubuntu on a virtual machine. When I made the account while installing, I made the password 2251, but now when I type the password in for installing updates, etc., it doesn't work. It's possible that I'm wrong, but I've tried every other password that I would use, & none of them work. How can I reset the password, or at least make another user account with equal administrative privileges?

---

### Post by Egi_Power on 2009-05-08
Hi!

Try the following:
[I]EDIT:
Open the Terminal:
**Applications -> Accessories -> Terminal**[/I]
```
sudo -i
```
It should log you in as root.
> root@*yourusername*-desktop:~#

Next step:
```
passwd *yourusername*
```
It should look something like this:
> root@*yourusername*-desktop:~# passwd *yourusername*
Enter new UNIX password:
Now you just enter the new password twice, and all should be well.
Don't forget to logout from root:
```
exit
```

Egi_Power

---

### Post by glotz on 2009-05-08
Reboot and select single user mode, that makes you root. Then input passwd <your username goes here> and select a new password.

---

