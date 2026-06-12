---
title: "checkgmail broke?"
date: 2008-07-18
forum: General Help
---

### Post by macstevejb on 2008-07-18
There appears to be an authentication issue with checkgmail which, upon start up, wont recognise my user name and password. It worked fine up until yesterday.

Is anybody else having this problem and if so, any ideas on a solution?

Many thanks :)

---

### Post by Malfet on 2008-07-18
> **macstevejb said:**
> 
Is anybody else having this problem and if so, any ideas on a solution?


I do have the same problem and also looking for the solution...

M.

---

### Post by marcb on 2008-07-18
Same here.

---

### Post by richrosa on 2008-07-18
This has happened before. GMail changes often and does weird stuff now and then. Someone (not me) will pick up a fix soon.

---

### Post by cpetercarter on 2008-07-18
Yes - we all seem to have this problem.
If you run ```
checkgmail -no_cookies
``` from the terminal, checkgmail will run, but without the options to delete etc messages.

---

### Post by Archimedes0212 on 2008-07-18
my checkgmail seems to be working fine.  have you enabled the save password button?

---

### Post by dn* on 2008-07-18
This bug is also present in Intrepid Ibex. Has a Launchpad bug been logged? I couldn't find one.

---

### Post by pt123 on 2008-07-18
same here

---

### Post by Thomaseov on 2008-07-19
> **macstevejb said:**
> There appears to be an authentication issue with checkgmail which, upon start up, wont recognise my user name and password. It worked fine up until yesterday.

Is anybody else having this problem and if so, any ideas on a solution?

Many thanks :)

Ditto

---

### Post by ptinolv on 2008-07-20
I also have this problem. It already happened to me some months ago. I tried the same commands, and it works :

```
cd /tmp
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo cp checkgmail /usr/bin 
```

I hope it will work for you too.

---

### Post by richrosa on 2008-07-21
This will work too. 

```


cd /tmp
svn co [https://checkgmail.svn.sourceforge.net/svnroot/checkgmail](https://checkgmail.svn.sourceforge.net/svnroot/checkgmail) checkgmail
cd checkgmail
sudo cp checkgmail /usr/bin

```

---

