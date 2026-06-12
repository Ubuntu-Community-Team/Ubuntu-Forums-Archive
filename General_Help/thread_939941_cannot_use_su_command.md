---
title: "cannot use su command"
date: 2008-10-06
forum: General Help
---

### Post by mahirh on 2008-10-06
when i use "su" command it shows
```
su: Authentication failure
```
after typing password

---

### Post by AllanPoe on 2008-10-06
Use "sudo" instead

---

### Post by kellemes on 2008-10-06
> **mahirh said:**
> when i use "su" command it shows
```
su: Authentication failure
```
after typing password

Just "su" will try to log you in as root by default, Ubuntu doesn't have the root-account enabled so "su" won't work since it is the same as "su root".
"su <username>" will work.

But as *AllenPoe* said.. use "sudo" instead.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Aximilli on 2008-10-06
I know this sounds odd, but I believe you need to try 'sudo su' to put yourself into root

---

### Post by Titan8990 on 2008-10-06
The equivalent of su in debain based distros is:

sudo -i

---

### Post by Tethylis on 2008-10-06
Are you sure your typing the correct password?

if your trying to become a root user try typing sudo su.

---

### Post by mahirh on 2008-10-08
> **Tethylis said:**
> Are you sure your typing the correct password?

if your trying to become a root user try typing sudo su.

thanks , it works

resolved

---

