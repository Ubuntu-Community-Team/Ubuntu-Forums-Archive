---
title: "[SOLVED] Package manager..."
date: 2008-10-28
forum: General Help
---

### Post by claymater on 2008-10-28
Ok, so I open the package manager, and get this message..


```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So I run "dpkg --configure -a" and get this... 

```
dpkg: requested operation requires superuser privilege

```


I dont know how to make myself a "superuser"... Help? :(

---

### Post by Sponzenbroekske on 2008-10-28
> **claymater said:**
> Ok, so I open the package manager, and get this message..


```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So I run "dpkg --configure -a" and get this... 

```
dpkg: requested operation requires superuser privilege

```


I dont know how to make myself a "superuser"... Help? :(


```
sudo dpkg --configure -a
```

OR  (THIS IS NOT NECESSARY FOR UBUNTU, TAKE THE "SUDO" COMMAND FOR UBUNTU)

```
su
```
THEN password
THEN ```
dpkg --configure -a
```

---

### Post by Portmanteaufu on 2008-10-28
"Superuser" just means "root". To run a command as root, just do: 

sudo command

or in this case: 

sudo dpkg --configure -a

You'll be prompted for your password before it runs.

---

### Post by oilchangeguy on 2008-10-28
> **claymater said:**
> Ok, so I open the package manager, and get this message..


```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So I run "dpkg --configure -a" and get this... 

```
dpkg: requested operation requires superuser privilege

```


I dont know how to make myself a "superuser"... Help? :(

type sudo dpkg --configure -a and press enter.

---

### Post by SunnyRabbiera on 2008-10-28
> **Sponzenbroekske said:**
> ```
sudo dpkg --configure -a
```

OR

```
su
```
THEN password
THEN ```
dpkg --configure -a
```

yes though the su command is not needed on ubuntu.

---

### Post by Sponzenbroekske on 2008-10-28
> **SunnyRabbiera said:**
> yes though the su command is not needed on ubuntu.

Sry didn't saw it was ubuntu :) I'll edit my post

---

### Post by claymater on 2008-10-28
Ok thanks guys! I got it to work! :D

---

