---
title: "delete home folder"
date: 2008-08-31
forum: General Help
---

### Post by belovedmonster on 2008-08-31
I deleted another user profile from my computer in "Users and Groups" but I am still left with their home folder. How can I delete it? The option is greyed out.

---

### Post by aloshbennett on 2008-08-31
When you delete a user, their home folders are not deleted. You can do this manually.
> sudo rm -rf /home/deleteduser

But be VERY VERY CAREFUL when you use sudo rm -rf. If you accidently delete something else, you'd be in trouble.

---

### Post by WRDN on 2008-08-31
You can delete the folder by typing:

```
sudo rm -rfI /home/[user]
```

I added the "I" so you will be prompted again before anything is deleted.

You can also delete it in nautilus, by typing:

```
sudo nautilus
```

Navigate to the folder, and delete it. Unless another user is in the same group, you may also want to delete the group for the user you deleted.

---

### Post by MatthewPlanchard on 2008-08-31
You've got to click on "Unlock" down at the bottom and enter your administrative password.

Then you should be able to delete other user accounts.

---

### Post by belovedmonster on 2008-08-31
I'm using Thunar not nautilus so I did it in the terminal. Thanks :)

---

### Post by BrBBL on 2009-12-21
I've mounted </home/username> directory to an other partition. Now I want to remove this directory from the old place.
```
sudo rm -rf /home/username
```is followed by
> rm: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1091;&#1076;&#1072;&#1083;&#1080;&#1090;&#1100;* `/home/hose/.gvfs': Permission denied(* - *unable to remove*)
```
sudo chmod -R 777 /home
```gives the same. What's the problem?

---

### Post by Leppie on 2009-12-21
> **belovedmonster said:**
> I'm using Thunar not nautilus so I did it in the terminal. Thanks :)

you can also run thunar in root mode:
```
$gksu thunar
```

---

### Post by BrBBL on 2009-12-21
Any thougts (post #6)?

---

### Post by sisco311 on 2009-12-21
> **BrBBL said:**
> Any thougts (post #6)?

Make sure that all your data is backed, log out from the GUI, Press Ctrl+Alt+F1, login in the virtual console and remove the old home directory. 

If you still can't delete the directory, then boot in *Recovery Mode* and remove it from there. 

Don't forget to mount your new home directory before you log back in.

---

### Post by BrBBL on 2009-12-21
> **sisco311 said:**
> Make sure that all your data is backed, log out from the GUI, Press Ctrl+Alt+F1, login in the virtual console and remove the old home directory. 

If you still can't delete the directory, then boot in *Recovery Mode* and remove it from there. 

Don't forget to mount your new home directory before you log back in.

I've removed an old directory from virtual console, but after reboot it has appeared again.

---

