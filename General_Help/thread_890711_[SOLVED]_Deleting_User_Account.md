---
title: "[SOLVED] Deleting User Account"
date: 2008-08-15
forum: General Help
---

### Post by uzzo2 on 2008-08-15
i need to know how to completely delete and then reinstall a user account due to a problem that i'm having with my wife's user account. the bottom panel disappeared and i was able to reinstall another panel but it still isn't working right. if you try to minimize something it just disappears and i just can't get it fixed. so i'm thinking at this point that maybe i need to delete it and start all over again, thanks in advance.

---

### Post by drs305 on 2008-08-15
System, Admin, Users & Groups. Unlock, highlight the user you want to delete and select Delete. Then Add User.  You might want to make a copy of her home folder to be able to restore specific configuration settings that will be lost once you delete her account.

---

### Post by uzzo2 on 2008-08-15
> **drs305 said:**
> System, Admin, Users & Groups. Unlock, highlight the user you want to delete and select Delete. Then Add User.  You might want to make a copy of her home folder to be able to restore specific configuration settings that will be lost once you delete her account.
ok, but when i tried to set it back up it won't let me enter the info back in. it says that the home directory already exists.

---

### Post by Archmage on 2008-08-15
If you want to get ride of the settings you need to delete the home folder (no need to delete the hole user).

If you want to delete all setting and file of the user simply do a:

```
sudo rm /home/usernameoftheuserthatyouhavedelete -R
```

It will ask you for a password and will delete everything.

PLEASE BE CAREFULL WHAT YOU TYPE!!!

---

### Post by uzzo2 on 2008-08-15
ok, thanks guys that seemed to do the trick, now just have to put all the bookmarks and all that stuff back on.

---

### Post by drs305 on 2008-08-15
> **uzzo2 said:**
> ok, but when i tried to set it back up it won't let me enter the info back in. it says that the home directory already exists.

You will still have to manually rename or delete the old home folder before creating a new user with the same name. Renaming it will allow you to copy settings to the new home folder if desired.
```
sudo mv /home/*oldusername* /home/oldusername-bak
```

... wonderin' why the past 2 messages didn't show for me for 8 minutes...

---

