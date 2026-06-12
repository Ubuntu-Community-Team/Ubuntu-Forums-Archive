---
title: "Installing a software manually vs. by apt-get"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by shelper on 2009-08-05
It has been confusing to me for a while
after i install a software abc manually
and when i do apt-get install abc
the command returns msg that abs is not installed yet.
which means the software is not registered to the package manager?

how can i update that so t apt-get does not return that msg?

the reason is, i installed a CVS version software abc
and i want to install another software abc2 which depends on abc
when i use apt-get install abc2, it says: u dont have abc, so, forces me to overwrite the cvs one......
thanks alot!

---

### Post by aysiu on 2009-08-05
It's best to install it with *apt-get* instead of manually.

Instead of summarizing the error message you get, can you paste in here *exactly* what command you used to install abc and *exactly* what error message you got in return?

It'd also help if you posted the output of these two commands: ```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by shelper on 2009-08-05
well 
the problem is:
the package from apt-get has bug and can not be installed correctly

here is the details
i installed emacs23 and want cedet for that so i did:
[CENTER]sudo apt-get install cedet[/CENTER]

the error msg is sth like this:
[CENTER]***.el:166:1:Error: Symbol's value as variable is void: outbuffer[/CENTER]

the cvs version does not have the problem
so i want to install ecb after i installed cvs version cedet by:
[CENTER]apt-get install ecb[/CENTER]

well, here is the output msg
[CENTER]The following NEW packages will be installed:
  cedet-contrib cogre ecb ede eieio semantic speedbar[/CENTER]
apparently, that is not want i want...

---

### Post by lykwydchykyn on 2009-08-11
I'm having the same problem trying to install cedet with the emacs-snapshot from the ppa.  I tried downloading cedet from sourceforge and it gives the same error, unfortunately.

Just waiting to see if there's a patch forthcoming.

---

