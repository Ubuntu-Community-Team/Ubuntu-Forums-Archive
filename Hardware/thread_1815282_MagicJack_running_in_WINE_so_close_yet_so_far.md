---
title: "MagicJack running in WINE so close yet so far"
date: 2011-07-31
forum: Hardware
---

### Post by matt3206 on 2011-07-31
Ok so I have a MagicJack which I have been trying to get working on the latest update of Ubuntu. Initially when I plug it in the device appears on the desktop, I open it up and try to autorun the executable file. And of course it pops up with an error message the .exe is blocked because it is untrusted blah blah blah. Well I tried and give it an executable permission using ```
chmod -R ugo+x magicJack
``` Without fail I get Read-only file system.
Ok so maybe if I copy the contents onto the desktop and try to edit the permissions using the same bit of code. what do you know it worked.
```
smith@laptop:~/Desktop/magicJack$ ls -l
total 720
-rwxrw-rw- 1 smith smith  28064 2010-09-14 02:48 autorun.exe
-rwxrw-rw- 1 smith smith  16158 2010-09-14 02:48 autorun.ico
-rwxrw-rw- 1 smith smith    308 2010-09-14 02:48 autorun.inf
-rwxrw-rw- 1 smith smith 684200 2010-09-14 02:48 autorunu.exe
``` I run the autorun and it appears that it will work. i see the magicjack loader and everything, untill i get an installer error that prompts me to retry or cancel the installation. Has anyone made it to this point and succeeded or am i just gonna be stopped at every turn?

---

### Post by sentinelace on 2011-08-06
I was hoping some results on this as well.  Only reason my one pc is windows is due to magic jack.  I need ubuntu so the kids don't get viruses :)

Wonder if we can run magic jack on a VM under ubuntu.  I would like to see if that would work.

---

### Post by .... on 2011-08-06
Works for me on Virtualbox: [http://magicjacksupport.com/finally-magicjack-on-linux-sort-of-t10970.html](http://magicjacksupport.com/finally-magicjack-on-linux-sort-of-t10970.html)

---

### Post by CR4ZYC on 2011-08-13
Maybe Someday they will offer Linux support.... their company has been skyrocketing....... I'll have to try your VM variation.

---

