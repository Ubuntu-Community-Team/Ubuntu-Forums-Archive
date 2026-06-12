---
title: "Problem with sudo"
date: 2005-11-09
forum: General Help
---

### Post by anaoum on 2005-11-09
Hello,

whenever i try to run something with sudo nothing happens. For example if i run "sudo apt-get update" it will just hang there doing nothing. i cant even use <control>c to get out of it, i have to close the terminal. this is having many effects on other software for me, i cant use totem and i cant open the system monitor. Could someone please tell me how to solve my problem.

Thanks.

---

### Post by anaoum on 2005-11-09
Problem Solved...

i removed sudo using apt as root, then reinstalled it.

Everything is back to normal

---

### Post by lorenco on 2005-11-09
Now if you were using windoze you would have to re-install I love this OS!

---

### Post by az on 2005-11-09
[QUOTE=anaoum]Problem Solved...

i removed sudo using apt as root, then reinstalled it.

Everything is back to normal[/QUOTE]
Great.  You could also have done itin one step:

apt-get install --reinstall sudo

---

