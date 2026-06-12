---
title: "Best way to setup Apache2 with Dreamweaver access?"
date: 2008-09-11
forum: General Help
---

### Post by underwater on 2008-09-11
Hello,

I know that by default Apache2 stores its web files in /var/www/ which is owned by root.  I need to give access to editing files on the web-server via Dreamweaver.  This means that the person should be able to edit a file in Dreamweaver, click the Put icon that is configured to use sftp to connect to the server, and then have it upload to the server and be live.

My first thought was to simply make different users be members of the www-data group, and then change the ownership and group of /var/www/ to www-data, but I feel like this is sort of clunky.

I thought I would ask the room for additional help. 

Has anyone here made a nice Dreamweaver setup?
Any recommendations or ideas?

---

### Post by Alaric on 2008-11-01
Try 
```

sudo chmod g+rw /var/www -R
sudo usermod -G ww-data <your-username-for-ftp>

```

P.S. you have to log out the users that you add to the www-data group before the changes will take effect

---

### Post by anystupidname1 on 2011-01-03
WARNING! The -G parameter for usermod will remove your user from groups that are not listed in the command unless used with -a. One or more users have shot themselves in the foot because of this.

[http://ubuntuforums.org/showpost.php?p=10312033&postcount=1](http://ubuntuforums.org/showpost.php?p=10312033&postcount=1)

---

