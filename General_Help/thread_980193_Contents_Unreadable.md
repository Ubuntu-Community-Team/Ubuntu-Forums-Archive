---
title: "Contents Unreadable"
date: 2008-11-12
forum: General Help
---

### Post by hyburn on 2008-11-12
for some reason I cant get into the folder through the file browser, but while in a terminal as root I can.

did I screw my system?

how do I reverse this error?

where can I read more about it, so it doesnt happen again?

---

### Post by john183 on 2008-11-12
your user login does not have permissions to read the contents of the folder. you need either through the terminal as root or through a "root" nautilus (assuming you are using Ubnutu and not a variant) change the permissions of the folder so that all users can see the contents. if you need help in doing this, let me know.

---

### Post by hyburn on 2008-11-12
yes please help

---

### Post by john183 on 2008-11-12
ok press alt+f2 and type the following
```
gksudo nautilus
```
it will ask you for your password and will then open a nautilus browser window with root privledges.
Navigate to the folder above the one that you are trying to get in to and right click on the problematic folder and choose properties.

On the permissions tab of the properties window look at the last drop-down menu. it probably just has "--" in it. click on it and choose one of the options, as you go down the list the selections each offer more capabilities to other users.

also while you are in the folder permissions you can change the owner to your login and the such.

Hope this helps.

---

### Post by Portmanteaufu on 2008-11-12
If the permissions are simply set too tightly, do:

```

sudo chmod 755 [directory name]

```

Then try to read it again using the GUI. If that doesn't work, try:

```

sudo chown -R <your user name>:<your group, usually "users"> [directory name]

```

---

### Post by john183 on 2008-11-12
> **hyburn said:**
> Bump help!! Cant change permissions!!!!!!!!

Man, seriously give people a chance to type. we didn't forget about you.

---

