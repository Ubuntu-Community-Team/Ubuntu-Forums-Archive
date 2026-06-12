---
title: "Problem Installing software"
date: 2008-08-07
forum: General Help
---

### Post by mr.moch on 2008-08-07
Whenever I try to install any applications in the terminal OR add/remove...., I get the following error:

"dpkg error: use dpkg --configure -a to fix."

If I put that in the terminal, I get:

> Must be superuser to perform this action <--I asummed "root".

So, after something weird happened, I was in ROOT.  I typed in the command, and it said that it could not find a file.  How can I get this fixed?  I am asking for help since I can't install/remove any applications using the dialaog or "sudo".

---

### Post by rraj.be on 2008-08-07
Had you tried this
```

sudo dpkg --configure -a

```
Sudo gives you the root privileges.

---

### Post by spiderbatdad on 2008-08-07
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by mr.moch on 2008-08-08
Thank you, both of you.  The 'sudo' command did work.  For some reason, I didn't think of it!

---

