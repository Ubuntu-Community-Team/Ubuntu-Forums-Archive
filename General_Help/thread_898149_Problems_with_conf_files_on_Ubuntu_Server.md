---
title: "Problems with conf files on Ubuntu Server"
date: 2008-08-22
forum: General Help
---

### Post by ToXiCaTIoN.d on 2008-08-22
I have a small bit of Linux knowledge, only apt-get sudo and nano are the commands I know.

I want to try Ubuntu server, and it's giving me some troubles. I've Googled a lot of things, although each tutorial I find it tells me to edit /ect/apache2/apache2.conf. Well, there is no file with that name.

```
sudo nano /ect/apache2/apache2.conf
```

That gives me a blank "document" with no text or anything, but it tells me to add something to the end of that document, but I can't because there is nothing in the document. So, do I have the folder for apache incorrect, or what's going on? I am using Ubuntu Server 8.04.

Thanks for your support.

---

### Post by Diabolis on 2008-08-23
Wrong:
```
sudo nano /ect/apache2/apache2.conf
```

Correct:
```
sudo nano /etc/apache2/apache2.conf
```

If you press 2 times the tab key, the terminal emulator will complete the commands. It helps to avoid typos like this one.

---

### Post by ToXiCaTIoN.d on 2008-08-23
Wow, thank you. I can't believe I missed that. I have a new problem now. I am unable to set the root password for mysql. I  used this code below:

```
mysqladmin -u root password new-passhere
```

This gives me:

> error: 'Access denied for user 'root@localhost' (using password: NO)'

I know that root usually doesn't come with a password but I am still not able to connect to mysql via phmyadmin.

---

