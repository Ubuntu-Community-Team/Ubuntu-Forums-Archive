---
title: "Changing my password?"
date: 2008-07-19
forum: General Help
---

### Post by lupinesoul on 2008-07-19
I've had someone working on my computer.  He's done now, so how can I change my password. (i.e. I'm the admin account)

---

### Post by dexter.deepak on 2008-07-19
if you are logged in as "username" :
```
passwd <username>
```

if you are not logged in as user, i.e you are changing password of other account:
```
sudo passwd <username>
```
when  prompted, give "your" password

---

### Post by sisco311 on 2008-07-19
from a terminal:
```
passwd
```

---

### Post by mike2357 on 2008-07-19
Assuming you're using Gnome:

System -> Administration -> Users and Groups

Click on your account name, click on Properties, and you'll see text boxes at the bottom to change your password.

---

### Post by Taxman415a on 2008-07-19
If you use the Gnome GUI method, In 8.04 I believe you have to click on the unlock button before you are able to click on properties and change the settings. You may not in this case, but you do in some.

---

