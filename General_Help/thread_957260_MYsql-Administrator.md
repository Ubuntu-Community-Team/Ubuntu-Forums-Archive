---
title: "MYsql-Administrator"
date: 2008-10-24
forum: General Help
---

### Post by Uchiha_madara on 2008-10-24
Hi every one

Note : I tried installing Mysql Administrator by using Add/remove Application's but this way have missing Packages " not Complete install"
so :


i need to install  MySql Administrator by :

1 - I need a link to download the program(.dev Package)
2 - I need to install it by terminal " i need the Code to Type it in the terminal)



Please help and thank you a lot

---

### Post by jespdj on 2008-10-24
You install packages from the terminal with the command **apt-get**. You need to do this with superuser privileges, so you need to type **sudo** in front of the command. The package for MySQL Administrator is called **mysql-admin**, as you can find on [http://packages.ubuntu.com](http://packages.ubuntu.com)

So the command to install it from the terminal is:
```
sudo apt-get install mysql-admin
```

---

