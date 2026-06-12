---
title: "User deleted"
date: 2008-11-20
forum: General Help
---

### Post by abhver on 2008-11-20
I created a user when I installed the ubuntu (8.10)
I had a lot of data under that user.
Now I created another user with admin rights and deleted the first one(which I created earlier during install). Now I am unable to accesss/copy the data of first user (that was deleted). 
Need help.

Thanks in adv,
Abhishek

---

### Post by FreeFull on 2008-11-20
Once data is deleted, you're unlikely to be able to get it back. Sorry.

---

### Post by tubezninja on 2008-11-20
Does the home directory of the old user still exist? (/home/username)

If not, then the data is pretty much gone.

---

### Post by lukjad on 2008-11-20
I'm not sure, but look up something called photorec. I haven't used it, but maybe it'll help. Hope you find what you are looking for!

---

### Post by abhver on 2008-11-20
only user is deleted not data

---

### Post by lukjad on 2008-11-20
Can you not recreate it?

---

### Post by LowSky on 2008-11-20
you have to change the permission of that folder
here the command
```
sudo chmod 777 -R */path/to/directory*
```

---

### Post by LowSky on 2008-11-20
here's the information on changing file permisions

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by abhver on 2008-11-20
> **LowSky said:**
> you have to change the permission of that folder
here the command
```
sudo chmod 777 -R */path/to/directory*
```



Thanks LowSky, the command has worked for me

---

