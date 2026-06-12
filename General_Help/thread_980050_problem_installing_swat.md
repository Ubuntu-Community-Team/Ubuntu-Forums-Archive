---
title: "problem installing swat ??????"
date: 2008-11-12
forum: General Help
---

### Post by washable mist on 2008-11-12
following the guide here [https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)........... a guide on installing swat for samba

i get to part three where i have to insert the code into terminal, all goes fine but when i go to save and exit i get a error message 
{error writing /ect/xientd.d/swat: no such file or directory.

i have refered to this guide before when installing swat but i seem to have come to a dead end here, any help with this would be greatly appritiated

---

### Post by -Zeus- on 2008-11-12
how did you quit?  i take it Ctrl+X + Y + enter?

---

### Post by Wayne_V on 2008-11-12
make sure /etc/xinet.d exists.  If it doesn't, 'sudo apt-get install xinetd'.

make sure you 'sudo vi /etc/xinet.d/swat' and not just vi.

and make sure you used xinet.d and not xient.d ....

---

### Post by Coreigh on 2008-11-12
TYPO ALERT!

> error writing /ect/xientd.d/swat: no such file or directory.

You have typoed the file name it should be xinetd.d. You have transposed the n and the e.

You also mistyped etc.

---

### Post by washable mist on 2008-11-12
thanks that was a big help, it was a typo that i made, silly me
thanks for the replys

---

