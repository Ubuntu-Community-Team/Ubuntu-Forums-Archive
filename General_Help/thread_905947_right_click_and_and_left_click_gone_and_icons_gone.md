---
title: "right click and and left click gone and icons gone"
date: 2008-08-30
forum: General Help
---

### Post by LukeRocksALot on 2008-08-30
i cant use right click or left click on the desktop,and all my icons are gone....dont know what happened...

---

### Post by cariboo on 2008-08-30
Go to System-->Administration-->Users And Groups and create a new user. Login as the new user and see if the problem persists. If every thing works the way it should, transfer all you files from your old home directory to the new directory. Once you have done this delete your old home directory, then rename the new user directory to your username like this in a terminal:

```
sudo mv /home/<newuser> /home/<username>
```

Where <newuser> is the user you just created, <username> is your user name. You will then have to change ownership of the directory, in a terminal type:

```
sudo chown -R <username>.<username> /home/<username>
```

If there are any problems, you can post in the same thread.

Jim

---

