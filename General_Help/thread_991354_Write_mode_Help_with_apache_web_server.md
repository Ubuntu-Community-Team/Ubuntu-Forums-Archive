---
title: "Write mode Help with apache web server"
date: 2008-11-23
forum: General Help
---

### Post by waloshin on 2008-11-23
I am setting up an Apache web server. I am trying to write some files mainly SMF forum files to the /var/www folder, but i dont have permission. How do i get around this. I am also trying to change the ip address in /ect/mysql/my.cnf ,


# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1

The bind-address to my ip address, and i get this error:

Could not save the file /etc/mysql/my.cnf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

I am trying to chmod 0777 directories /var/www and /ect/mysql ,but it says there is not such directory?

Help please!

---

### Post by beno1990 on 2008-11-23
Your normal account doesn't have the permission to edit configuration files in /etc. To get around this, try the following command:

```

sudo gedit /etc/mysql/my.cnf

```

---

### Post by spiderbatdad on 2008-11-23
> **beno1990 said:**
> Your normal account doesn't have the permission to edit configuration files in /etc. To get around this, try the following command:

```

sudo gedit /etc/mysql/my.cnf

```

At times like this, someone must always complain, the appropriate command for launching graphical applications as root is: gksu...hence:
```
gksu gedit <file>
```

---

### Post by mbeach on 2008-11-23
> **waloshin said:**
> 
I am trying to chmod 0777 directories /var/www and /ect/mysql ,but it says there is not such directory?

note that it is /**etc**/mysql

---

