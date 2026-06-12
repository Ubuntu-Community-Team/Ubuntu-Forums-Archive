---
title: "[SOLVED] Need to create an administrator account"
date: 2008-08-07
forum: General Help
---

### Post by Rakanishu on 2008-08-07
I installed my copy of Ubuntu, and set the "admin" account to the name administrator. Not the root account, mind you...

Now I wasn't happy with the name, so I removed it through "Users and Groups". But now I can't create a new one, since the administrator account was the only account that could create new users and modify.

How do I do to get a new administrator account?

Thanks in advance.

---

### Post by sisco311 on 2008-08-07
reboot in recovery mode and from the 
root shell create a new account and add
it to admin group:
```
useradd *username*
```
```
adduser *username *admin
```
```
reboot
```

---

### Post by Rakanishu on 2008-08-08
Thanks for your answer, but that didn't help entirely.

After creating the user, I can't login with it, because I leave the password box empty. But there is no password for the user!
How do I create a password for an administrator account, with root?

---

### Post by pmlxuser on 2008-08-08
why don't you try adding user using the System > Administration > Users and Groups > Add user

The graphical adding gives you all you need.... unless you are familiar with command prompt try to do things the easier way with GUI

;)

---

### Post by cdtech on 2008-08-08
> **Rakanishu said:**
> Thanks for your answer, but that didn't help entirely.

After creating the user, I can't login with it, because I leave the password box empty. But there is no password for the user!
How do I create a password for an administrator account, with root?

When you get to the "GRUB Boot Screen" press escape.
Press "e" to edit.
Highlight the line that begins with kernel <kernel number>, press "e" to edit.
Go to the very end of the line and add "rw init=/bin/bash".
Press enter, then press "b" to boot your system.
Your system will boot into a passwordless root shell.

**CAUTION:** This is a **"FULL ROOT SHELL!"** You could damage your system if your not careful!
Type in passwd <username>. To set your password for the user.
Type "reboot".

Hope this helps.....

---

### Post by WRDN on 2008-08-08
> **Rakanishu said:**
> Thanks for your answer, but that didn't help entirely.

After creating the user, I can't login with it, because I leave the password box empty. But there is no password for the user!
How do I create a password for an administrator account, with root?

To add a password, type:

```
passwd [username]
```

Replace "[username]" with the username you entered.

---

### Post by Rakanishu on 2008-08-08
I changed password, and now I can almost login with the user, but I get the following message:

> Home directory does not exist. Login with root home dir?
Unlikely anything will work unless in failsafe mode.

I press YES and get following:

> User's $HOME/.dmrc file being ignored. This prevents the session from saving.
File should be owned by user and have 644 permissions.
Home directory must be owned and not writable by others.

I then get back to the login screen.


Oh, and doing it through the Users and Groups doesn't work, since I can't create folders and give permissions with that.

---

### Post by mikjp on 2008-08-08
Well, reinstalling Ubuntu takes 20 minutes. It is probably the quick and dirty solution :-)

Greetings,

mikko

---

### Post by jffourie on 2010-05-13
Hi there i just would like to know if you can add a new user and their password on the same command line.

---

