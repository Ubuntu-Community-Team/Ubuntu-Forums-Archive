---
title: "how to install My SQL and PHP in Ubuntu"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by sundarrajan on 2009-02-02
I m in a project which leads me to create a database driven website using My SQL and PHP.

I m unfamiliar about that but i know SQL  and having knowledge in HTML,XML etc to create a website. I 'm totally unfamiliar about PHP.

So just give me an intro about that or help me how it is useful or help in some other alternative ways!!!

---

### Post by mcduck on 2009-02-02
The best and easiest way is to open Synaptic Package Manager, then go to Edit/Mark Packges by Task and select "LAMP server". Then click "Ok" and finally "Apply" in Synaptic. This will install & configure Apache2, MySQL and PHP5 for you automatically.

You may want to also install phpmyadmin to get a graphical interface for MySQL.

and here's the command-line way of doing the same:
```
sudo tasksel install lamp-server
sudo apt-get install phpmyadmin
```

---

### Post by 92fs on 2009-02-02
> **mcduck said:**
> The best and easiest way is to open Synaptic Package Manager, then go to Edit/Mark Packges by Task and select "LAMP server". Then click "Ok" and finally "Apply" in Synaptic. This will install & configure Apache2, MySQL and PHP5 for you automatically.

You may want to also install phpmyadmin to get a graphical interface for MySQL.

and here's the command-line way of doing the same:
```
sudo tasksel install lamp-server
sudo apt-get install phpmyadmin
```

Thanks mcduck, easy as pie.

---

