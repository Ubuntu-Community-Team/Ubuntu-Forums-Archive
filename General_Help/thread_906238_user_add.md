---
title: "user add"
date: 2008-08-31
forum: General Help
---

### Post by nik1990 on 2008-08-31
can som 1 plz give me all the user add commends in ubuntu to make a new user

---

### Post by Scunge on 2008-08-31
Assuming Hardy...

Go to **System > Administration > Users and Groups**, click "**Unlock**" and enter your password. Click "**Add User**", and enter the new account details. The username is the only thing you have to have, everything else is optional, but usually you will want to set a password as well.

Then on the command line, (**Applications > Accessories > Terminal**), enter:
```
sudo chmod 750 /home/<username>
```
where "<username>" is that which you chose above, and you'll need to supply your own password again. This command prevents other users from seeing that user's files (which Ubuntu allows by default).

You may want to do that with your username as well!

Note: the command line for creating the user, if you wanted to do it all that way, is
```
sudo adduser <username>
```

---

### Post by overdrank on 2008-08-31
Hi and if this is the same issue as 
[http://ubuntuforums.org/showthread.php?t=904320](http://ubuntuforums.org/showthread.php?t=904320)
You will need to see the person who has administrative on your system

---

