---
title: "problim with xampp install"
date: 2008-09-28
forum: General Help
---

### Post by THE BLUE DRAGON on 2008-09-28
hi guys 
i download from [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374)
then i go to install it 
i writ tar xvfz xampp-linux-1.6.7.tar.gz -C /opt in termnal 
but when i clich enter 

tar: xampp-linux-1.6.7.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

why ???? 

xampp-linux-1.6.7.tar.gz i download it in home folder

---

### Post by THE BLUE DRAGON on 2008-09-28
guys i am wait 1 hour and no answer

---

### Post by THE BLUE DRAGON on 2008-09-28
guys now i wait more 2 hour and no answer why???

---

### Post by louieb on 2008-09-28
Try prefixing the tar command with **sudo** that will allow the command to run with root user privileges.

```
sudo tar xvfz xampp-linux-1.6.7.tar.gz -C /opt
```BTW: the forum has a 24 hour bump rule. That is you can get an infraction by bumping your post more often that once a day.

Xampp is ok but another way to install a lamp server is
```
sudo tasksel install lamp-server
``` [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

