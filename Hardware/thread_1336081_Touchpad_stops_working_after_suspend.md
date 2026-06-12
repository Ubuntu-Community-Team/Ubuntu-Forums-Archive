---
title: "Touchpad stops working after suspend"
date: 2009-11-24
forum: Hardware
---

### Post by lobstar on 2009-11-24
Hi

I have a Lenovo 3000 y310. Installed Ubuntu 9.10 (by wubi) recently. 

Everytime my machine goes out of suspend the Touchpad has been disabled.

Any suggestion how to fix this?

Thanks

---

### Post by garvinrick4 on 2009-11-24
Wubi just does not like suspend, hibernate at all. Just do not use
them. Ubuntu seems to be pretty good with touchpad software. Better
than Microsoft. Remember you are in a folder inside of your Windows
install. Just like an app right next to users in the c: drive.
 You understand in Wubi you are host in the nautilus filesystem icons. Host is actually the C; drive in Windows.

If you have trouble with shutdowns or reboots. Use the Terminal
"sudo shutdown -r now to reboot", "sudo shutdown -h to shutdown" without the qoutes. Wubi is great to learn on, really nice for that purpose. When you feel good about your skills partition and do a dual install with the same iso copy you did your wubi. The software
now a days does most all of it for you. Just nice to have seperate 
partions and seperate grubs. 
Wubi uses windows dos4grub and attaches itself to that.
Enjoy you linux.

---

### Post by lobstar on 2009-11-25
Thanks for your answer.

I guess it is about time I show what I am made of and do the partitioning.

---

### Post by lobstar on 2009-11-28
Making a "real" install did not help. Touch pad still dies after suspend.

Do i need to install some other driver?

---

### Post by oooh on 2009-12-07
Check this people:

[http://ubuntuforums.org/showthread.php?t=1314835&highlight=touchpad+hibernate&page=2](http://ubuntuforums.org/showthread.php?t=1314835&highlight=touchpad+hibernate&page=2)

---

### Post by Willynux on 2010-11-21
This was the solution that worked for me
[http://ubuntuforums.org/showthread.php?p=10145996#post10145996](http://ubuntuforums.org/showthread.php?p=10145996#post10145996)

(problem was occurring only with one user, once i logged, or tried to log into account)

---

### Post by lobstar on 2011-02-12
None of the suggestions worked.

Any other ideas?

---

