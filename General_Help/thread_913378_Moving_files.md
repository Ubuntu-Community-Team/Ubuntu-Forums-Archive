---
title: "Moving files"
date: 2008-09-07
forum: General Help
---

### Post by CheeseAndToast on 2008-09-07
Sorry if this sounds stupid.....

I'm trying to move some movies from my user folder to my kids folder....i don't have permissions?

I thought I was the administrator.

Can someone help please?

Thanks

---

### Post by forger on 2008-09-07
You probably are, but you have to 'gain' the privileges by typing in the password and using the program as an authenticated administrator

Fire up Applications > Accessories > Terminal
execute this:
```
gksu nautilus
```
Type in your password and then you can do whatever you want

---

### Post by lukjad on 2008-09-07
Try this: 
Go to Applications->Accessories->Terminal.
After the terminal is open, copy/paste:
```
gksudo nautilus
```

Enter your password when asked.

Then, when Nautilus is open press Ctrl+L and type:
```
/home
```
and hit enter. You should then see your home folder and your child's home folder. Go into yours, right click and select copy the file. Then hit Ctrl+L and type 
```
/home
```

Then go into your child's folder and right click paste. The fild should be copied unless there is something wrong. 

Tell us how it goes.

(I hope I didn't make this too complex.)

---

### Post by ad_267 on 2008-09-07
You can also press Alt+F2 to get the run dialog and run "gksu nautilus"

---

### Post by ryanhaigh on 2008-09-07
Rather than running as root every time you want to move movies over to the kids folder you might try changing the permissions on the moviies folder in your kids home directory to allow anyone to write to that directory.

To do this you can run nautilus as root, as instructed above, and right click>properties>permissions on the directory you want to move the videos to changing the permissions to read and write for all users.

---

