---
title: "&quot;Main Menu&quot; won't open"
date: 2008-07-31
forum: General Help
---

### Post by dschaller on 2008-07-31
I cannot get System>Preferences>Main Menu to open. When I click on it, nothing happens. I'm trying to edit the menus. Does anyone have any ideas?

---

### Post by tuxxy on 2008-07-31
Try and run from the terminal, type this command

```
alacarte
```

---

### Post by Potatoj316 on 2008-07-31
try right clicking on the menus and choosing edit

---

### Post by dschaller on 2008-07-31
Ok. It will open from the terminal, but only when I start it as root. Is this typical behavior?

---

### Post by dschaller on 2008-07-31
> **Potatoj316 said:**
> try right clicking on the menus and choosing edit

This does not work either. Same result. Nothing opens.

---

### Post by tuxxy on 2008-07-31
> Ok. It will open from the terminal, but only when I start it as root. Is this typical behavior?

No this is not typical behaviour but atleast you got your menu back now?

---

### Post by drs305 on 2008-07-31
As a user, try running 'alacarte' from terminal and see if you have a "*Revert*" button available. That might restore the user menu for you.

---

### Post by dschaller on 2008-07-31
Yes, I can open alacarte when I am root. Here is the error I get as a regular user:

IOError: [Errno 13] Permission denied: '/home/dschaller/.config/menus/applications.menu'

Is seems like a permission setting got changed somewhere? I'm not too good with permissions. Could I change it back to what it's supposed to be?

---

### Post by Potatoj316 on 2008-07-31
perhaps thats why its not running when he goes to open it the "normal" way, the permissions are not correct.  What file keeps track of your menus?

---

### Post by tuxxy on 2008-07-31
Navigate to **/home/user/.config/menus/** right click the file **applications.menu** and select **properties**

Now click on** permissions** and make sure that **owner access - execute option** is set to **read & write**

---

### Post by Potatoj316 on 2008-07-31
this command should do that as well.  
```
chmod u+rw /home/user/.config/menus/applications.menu
```

---

### Post by Separ on 2008-07-31
You could use chown and chmod from the terminal on the .config directory.
```
sudo chown -R username:username /home/username/.config
sudo chmod -R 700 /home/username/.config
```

---

