---
title: "root"
date: 2008-09-13
forum: General Help
---

### Post by m4k4v3l1 on 2008-09-13
I'm trying to change from sudo to root , with sudo passwd root , then i type su enter password , but I get this error:
Your account has expired; please contact your system administrator
su: User account has expired
Help?
BTW , I installed apache , mysql and php , but I want to delete them , how?

---

### Post by tekky on 2008-09-13
Try sudo passwd -u root. The lock behavior is controlled by whether or not the second field of /etc/shadow starts with "!" or "!!" (locked) or "$" (unlocked). You can fix it by hand using "sudo vipw" if you have to; that will edit /etc/passwd first and /etc/shadow second.

In generally a combination of "sudo" for individual commands, "sudo -i" for multiple comamands, and "gksu ..." for GUI programs can let you do everything you need without enabling the root account. On Ubuntu I hardly ever enable root.

---

### Post by hyper_ch on 2008-09-13
forum policies forbid to say how to enable root.

---

### Post by m4k4v3l1 on 2008-09-13
ok , I used gksudo and I did everything I wanted , now I want to put a password on mysql server , but it doesn't allow me , I use this command:
mysqladmin *u root password mypassword
but I get error:
mysqladmin: connect to server at 'localhost' failederror: 'Access denied for user 'root'@'localhost' (using password: NO)'

---

### Post by bodhi.zazen on 2008-09-13
> **m4k4v3l1 said:**
> I'm trying to change from sudo to root , with sudo passwd root , then i type su enter password , but I get this error:
Your account has expired; please contact your system administrator
su: User account has expired
Help?
BTW , I installed apache , mysql and php , but I want to delete them , how?

This is a bug on both debian and Ubuntu systems, do a google search.

There is rarely a need to set a root password, just use sudo -i.

---

### Post by m4k4v3l1 on 2008-09-13
Ok , I got a little confused , but now it's all good , last question:
How to delete apache , mysql , php5 from ubuntu?
I don't need to set a password now.

---

### Post by bodhi.zazen on 2008-09-13
How did you install them ?

Assuming you used apt-get :

[code]sudo apt-get remove --purge apache  mysql php5]/code]

---

