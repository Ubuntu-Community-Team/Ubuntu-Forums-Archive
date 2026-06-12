---
title: "user add"
date: 2008-08-31
forum: General Help
---

### Post by spiroman on 2008-08-31
can som one send me all the user add commends soo i can make a user with password

---

### Post by spiroman on 2008-08-31
can som one send me all the user add commends soo i can make a user with password

---

### Post by WRDN on 2008-08-31
To add a user:

```
adduser [username]
```

To give the account a password:

```
passwd [username]
```

---

### Post by spiroman on 2008-08-31
what is root it seas Only root may add a user or group to the system.

---

### Post by WRDN on 2008-08-31
To use "adduser", you must have root privileges, so type "sudo" before the command(s). You can use the command "[useradd]("http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/")" to add a user without needing these privileges.

---

### Post by Dutch70 on 2008-08-31
Type this ```
sudo
``` in front of the commands. and it will log you in as root. It is the same as admin. You will have to put in your password.

Dutch

---

### Post by ssam on 2008-08-31
simplest use is
```
adduser sam
```
to add a user called sam. it will then ask for any extra info such as a password.

to read its full manual run
```
man adduser
```
(this works for any command)

if you dont want to use the command line you can add a user with System->Administration->Users and Groups.

---

### Post by arkara on 2008-08-31
> **spiroman said:**
> can som one send me all the user add commends soo i can make a user with password

ok
if you want to add a user give
```
useradd -m -G users username
```
with this command you will create a home folder plus add the new user to the users group.
then run
```
passwd username
```
to append a password to the new user.
to see all the options
```
man useradd
man usermod
man groupadd
man groupmod
```

---

### Post by overdrank on 2008-08-31
Please do not make multiple threads on the same issue. And if I may ask what is the issue.
Threads merged.

---

