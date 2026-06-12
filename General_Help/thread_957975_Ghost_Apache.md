---
title: "Ghost Apache"
date: 2008-10-24
forum: General Help
---

### Post by Guardian-Mage on 2008-10-24
I have manually compiled apache, then I apt-got mysql and php5. Now however, my own Apache will not run, saying port 80 is in use. Sure enough, localhost takes me to /var/www while my apache is set up to load /home2/

No instances of Apache are running in the system manager. I am using the RC of 8.10 Ubuntu. How can I trace this problem?

EDIT: found a lot of config files in /etc/apache2 that point to port 80 and /var/www
How can I delete this version of apache?

---

### Post by pdwerryhouse on 2008-10-24
Run the following to see what process is using port 80:

```
sudo netstat -lpt | grep :www
```

It will probably be apache, in which case, you can remove it with:

```
sudo apt-get remove apache2.2-common
```

(...I chose apache2.2-common because I don't necessarily know which apache2 package you have installed, and this will remove anything that depends on apache2.2-common)

---

