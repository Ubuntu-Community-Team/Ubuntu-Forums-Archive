---
title: "Error moving file: Permission denied"
date: 2008-09-17
forum: General Help
---

### Post by evergreen_p on 2008-09-17
Im trying to install a plug in for amsn however when i try to drag the file into the plugins folder i get an error message.

Error while moving

under details

Error moving file: Permission denied

please help. im new to Linux

---

### Post by drs305 on 2008-09-17
You can't do that as a normal user as you are trying to move something into a system folder/file. To gain access, you have to use administrator privileges. Do that by opening nautilus with:
```
gksu nautilus
```

Enter your password (Edit: actually, you WILL see it as you type in a GUI app) and hit enter. You can now move files into system folders, just be careful.

Take a look at this link, which explains Root and Sudo:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by akhil.t on 2008-09-22
Thank you drs305. That helped!

---

### Post by Earl-Grey on 2010-02-17
> **drs305 said:**
> You can't do that as a normal user as you are trying to move something into a system folder/file. To gain access, you have to use administrator privileges. Do that by opening nautilus with:
```
gksu nautilus
```Enter your password (you won't see it as you type) and hit enter. You can now move files into system folders, just be careful.

Take a look at this link, which explains Root and Sudo:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

That code also helped me out a lot. Thank you :popcorn:

---

### Post by LilJoker52793 on 2010-11-15
[SIZE=4][FONT=Times New Roman]Well, I tried the code and I still can't move my files.. Why is this?
[/FONT][/SIZE]

---

### Post by chunky bacon! on 2011-01-24
> **drs305 said:**
> You can't do that as a normal user as you are trying to move something into a system folder/file. To gain access, you have to use administrator privileges. Do that by opening nautilus with:
```
gksu nautilus
```Enter your password (you won't see it as you type) and hit enter. You can now move files into system folders, just be careful.

Take a look at this link, which explains Root and Sudo:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")


Just a bump to thank this author for the tip.  Helped me, as well.

---

### Post by brenodamata on 2011-04-11
> **drs305 said:**
> You can't do that as a normal user as you are trying to move something into a system folder/file. To gain access, you have to use administrator privileges. Do that by opening nautilus with:
```
gksu nautilus
```

Enter your password (you won't see it as you type) and hit enter. You can now move files into system folders, just be careful.

Take a look at this link, which explains Root and Sudo:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

WOW, that was niceee!!
thanks a lot

---

### Post by madmathigan on 2011-05-24
Another newbie thanking you!  Just saved me a lot of headache.

---

### Post by Simon2212 on 2011-07-03
i try as well to move a file, but error keeps coming up.
and i wonder, what is nautilus ?? :P

---

### Post by CatKiller on 2011-07-03
> **Simon2212 said:**
>  what is nautilus ?? :P

The file manager.

---

### Post by Simon2212 on 2011-07-03
Thanks :D

---

### Post by Rocket2DMn on 2011-07-03
Please don't post in old threads, start a new one for your problems in the future. Thanks and welcome to Ubuntu!

---

