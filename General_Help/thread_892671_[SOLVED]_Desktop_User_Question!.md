---
title: "[SOLVED] Desktop User Question!"
date: 2008-08-17
forum: General Help
---

### Post by Rytron on 2008-08-17
Hi,
I have an account on my computer.
I have created a Desktop profile user account for other users on my computer. However I notice that from that account they can still access my user account via the home folder and can view and delete my files. What must I do to prevent others from accessing my account files?

I tried creating an unprivileged profile user account but this wont allow other users to access the internet.

Any suggestions? 
Thanks.

---

### Post by WRDN on 2008-08-17
To do this, you could remove the read privileges for the folder(s), using the "chmod" command:

```
sudo chmod -R -r /home/[user]
```

This should be done in the user account that you want to block access to, and it will remove the read privileges for them for the folder you specify.

---

### Post by sisco311 on 2008-08-17
> **WRDN said:**
> To do this, you could remove the read privileges for the folder(s), using the "chmod" command:

```
sudo chmod -R -r /home/[user]
```This should be done in the user account that you want to block access to, and it will remove the read privileges for them for the folder you specify.
There is no need to remove the permissions recursively.
```
chmod 0750 $HOME
```
or
```
chmod 0700 $HOME
```will do the trick.

---

### Post by Rytron on 2008-08-19
> **sisco311 said:**
> There is no need to remove the permissions recursively.
```
chmod 0750 $HOME
```
or
```
chmod 0700 $HOME
```will do the trick.

Hi sisco311,
I went with your suggestion.
Works like magic!

:popcorn:

---

