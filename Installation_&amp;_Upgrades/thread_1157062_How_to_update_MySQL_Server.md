---
title: "How to update MySQL Server?"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Endlesskiss on 2009-05-12
Hey everyone.

I've installed MySQL Server using the apt-get install mysql-server command, I got MySQL version 5.0.x, while the newest stable version is 5.1.x, How do I remove the current MySQL Server without killing my DB, and then install MySQL Server 5.1.x? [I know how to compile this from source, but then, how can I remove it?]


Thanks from advance!

---

### Post by unutbu on 2009-05-12
Back up your DB. I don't think backing up is strictly necessary, but I could be wrong.
Then remove mysql-server-5.0:
```

sudo apt-get remove mysql-server-5.0
```

and install version 5.1.

PS. Just out of curiosity: What is the reason for the upgrade?

---

### Post by Endlesskiss on 2009-05-12
> **unutbu said:**
> Back up your DB. I don't think backing up is strictly necessary, but I could be wrong.
Then remove mysql-server-5.0:
```

sudo apt-get remove mysql-server-5.0
```and install version 5.1.

PS. Just out of curiosity: What is the reason for the upgrade?


MySQL 5.0 with Apache2 = HIGH CPU [average 117% on mysqld process].

anyway, in case I want to delete the compiled binaries of the MySQL [which i'm going to install], how am I going to do this?

I don't think apt-get remove is going to do the job, is it?

and if it will, what will be the command?

---

### Post by unutbu on 2009-05-12
checkinstall is a package in the official repository. It can monitor the "make install" command and create a deb package instead of having the files installed directly.

If the normal command to install is
```

sudo make install
```

then instead do this:
```

sudo checkinstall -D --fstrans=no make install
```

You will be asked a few simple questions, and be given a deb package in return.
You can then install the deb package with
```

sudo dpkg -i PACKAGENAME.deb
```
and you can remove it with```

sudo dpkg -r PACKAGENAME
```

---

