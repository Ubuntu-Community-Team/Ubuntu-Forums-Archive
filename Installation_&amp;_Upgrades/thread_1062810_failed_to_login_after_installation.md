---
title: "failed to login after installation"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by bivi on 2009-02-07
Hi,
I just installed Ubuntu 8.10 in my PC.After entering the username and password a yellow screen is coming up and it stays for long time.Please share ur valuable inputs on this problem.

I am using a pentium 4 system with 256 MB of RAM.It has also Windows XP in it.

Thanks in advance

---

### Post by taurus on 2009-02-07
Did you install Ubuntu on it own partition or did you install it from windows, wubi?

---

### Post by bivi on 2009-02-07
Dear Taurus,
I did it on a seperate partition

---

### Post by taurus on 2009-02-07
Have you made any changes (window manager) the last time you used it?

At the GUI login screen, press <Ctrl><Alt>F2 to get to another console.  Log in with your username and password.  You could remove those Gnome config files (unless you have some personal settings that you want to save).  Then when you login again from GUI login screen, it will recreate them for you.  See if that works.

```
rm -rf .gconf .gconfd .gnome2
```
Then type exit to log out of that session.  Press <Alt>F7 to bring back the GUI login screen and log in.

---

### Post by bivi on 2009-02-07
Dear Taurus,
Thank you very much for your response.
But I am sorry that even it did not help.The same yellow screen is appearing.
Also when I type in the screen that you specified,I feel that the characters appear a lot late after I actually typed.

---

### Post by avtolle on 2009-02-07
Do you know what your graphics card is? Get to a console as above and do ```
lspci
```and copy/paste it here.

---

### Post by bivi on 2009-02-08
Dear Avtolle,
Intel 82845G/GL Chipset Integrated Graphics Device

---

