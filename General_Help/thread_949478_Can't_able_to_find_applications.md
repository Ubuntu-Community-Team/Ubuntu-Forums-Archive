---
title: "Can't able to find applications"
date: 2008-10-16
forum: General Help
---

### Post by rams123 on 2008-10-16
I installed antidialer.deb package manually by downloading and installed that , but the problem is I am not able to find that app in start menu ! Where i can find and open that?

---

### Post by cl0ckwork on 2008-10-16
try typing antidialer into the terminal to see if it runs correctly

---

### Post by rams123 on 2008-10-16
Tried but no result

---

### Post by Ayuthia on 2008-10-16
You can try and see where the the file antidialer is found in the system (from the Terminal):
```
sudo updatedb 
locate antidialer
```

You might even try the command:
```
which antidialer
```It will search through the executable paths and see if it can find it.

If the application works but you are unable to find it in the menu, you can update it by right clicking on the menu button and select menu editor and add it into the menu.

---

### Post by Ayuthia on 2008-10-16
Double-post.

---

