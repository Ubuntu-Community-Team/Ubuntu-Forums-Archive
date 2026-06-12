---
title: "restoring ubuntu?"
date: 2008-07-22
forum: General Help
---

### Post by hezuo on 2008-07-22
Hi there,
First off, I must sayt I'm a newbie, and I do need help. I tried to install wine 1.1.1 in ubuntu hardy, but after some hours I gave up. However, now it cannot load the gnome panel, the session manager appears and it just go black. I tried enter in the command line mode, and when I try to load a program, it says that the gtk is not initialized. 
Is there any way to restore the configuration to the state before I messed it up? or i have to reinstall ubuntu? thx  for your help.

---

### Post by tech0007 on 2008-07-22
You could either create a new user account or reinstall ubuntu.

sudo useradd [newuser]

---

### Post by Taxman415a on 2008-07-22
What instructions did you try to follow to install wine? If you followed the ones from winehq they should work and not cause problems. :)

---

### Post by hezuo on 2008-07-22
I followed the instructions (by the way it takes a life to install) but at the end it showed that my pc lacks of xml devel package.  I tried to install it manually, but i think i'm gonna wait untill a deb package is developed. I'm gonna try the user add. I wouldn't like to reinstall because all my programs are customized :( by the way, i'm using it on wubi.

---

### Post by CatKiller on 2008-07-22
You might try renaming your Home folder to user.old to see if a new (non-broken) Home folder gets created when you log out and log back in, and then copy the config files from the old Home folder to the new.

To keep up-to-date with Wine, you just need to add their repository to your sources.list. There are instructions on the winehq site. Using their repo, I'm running 1.1.1~winehq0~ubuntu~8.04-0ubuntu1

---

### Post by Taxman415a on 2008-07-22
I was hoping you'd link to which instructions you followed. Without knowing some details about what method you used, it's hard to know what to tell you. It is taking forever because you're compiling from source or did you add the repository and it's taking a long time to download everything?

---

### Post by hezuo on 2008-07-30
well, in the end i had to reinstall the whole system. thanks anyway.

---

### Post by Taxman415a on 2008-07-30
Did you get wine working this time I hope?

---

