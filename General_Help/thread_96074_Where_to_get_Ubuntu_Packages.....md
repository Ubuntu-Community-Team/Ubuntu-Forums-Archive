---
title: "Where to get Ubuntu Packages...."
date: 2005-11-28
forum: General Help
---

### Post by naseermughal on 2005-11-28
Hi there,

can anyone help me finding the Ubuntu packages....

i want to run, PHP, MySQL server on Ubuntu....

Plz also tell me of the packages extensions...

thanx in advance...

naseer

---

### Post by 23meg on 2005-11-28
You don't need to download the packages and install them, just use Synaptic to do it. Launch Synaptic and do a search for "php" and "mysql".

---

### Post by naseermughal on 2005-11-28
Thanx for help

can u tell me how can i launch Synaptic....

---

### Post by 23meg on 2005-11-28
System / Administration / Synaptic Package Manager.

---

### Post by naseermughal on 2005-11-28
thanx buddy

i will try, this options  and let u know about this, if i got any problem...

i am asking these small things, becoz i am new on linux os, my friend gifts me its cd, so i was trying it.....

anyway, once again, thanx....

---

### Post by penguinman007 on 2005-12-01
I think I installed MySql,

There is no MySql icon anywhere though, and no link in my programs group, there is no programs group.

There is a mysql folder in /etc

Inside that are some icons, when I click them, nothing happens.

Does anyone know where to get the MySql database application and MySql client that does stuff ?

---

### Post by Bachstelze on 2005-12-01
run this in a terminal : 

```
mysql -h *host* -u *user* -p
```

---

### Post by pertti on 2005-12-01
The MySql server starts automatically after you install it. If not, go to System > Administration > Services and see if it's checked.

You could also install mysql-admin and mysql-query-browser. They're two graphical frontends to the MySql server, and may be helpful if you're starting with MySql.

---

### Post by penguinman007 on 2005-12-01
Awesome,

Everything is starting to make sense.

evil laugh.

---

