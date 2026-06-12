---
title: "Regular users reading /var/www/ directory"
date: 2008-11-10
forum: General Help
---

### Post by Phases on 2008-11-10
Can I make my /var/www/ directory only readable by me/root? 

I ask because my box has a couple users other than myself, and they can go in there and read anything.. including my dbconnect file for SQL and what not. 

Can I make it readable only by my account, and/or root - and still have apache be able to show it to the world on the intertubes?

Thanks for any advice.

---

### Post by Sam on 2008-11-10
You can do this by giving access to /var/www directory only to Apache, then disabling worldwide read access.

```
sudo chgrp www-data /var/www
sudo chmod 750 /var/www
```


Or another solution is to give the same access to sensible files only. This let other users to browse the www tree, if you wish.

```
sudo chgrp www-data /var/www/path/to/password.config
sudo chmod 640 /var/www/path/to/password.config
```

---

### Post by Phases on 2008-11-10
That did the trick, thanks much! 

+1 thanks for you. ;)

---

