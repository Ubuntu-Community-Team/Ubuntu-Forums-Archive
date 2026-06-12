---
title: "Help Installing Packages"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by mandoxv on 2009-02-08
I keep getting this message:

Only one software management tool is allowed to run at the same time.

but im not running any other management tool.

I get this message when I try to install any package can anybody help? thank you.

---

### Post by taurus on 2009-02-08
Maybe the update manager is running in the background.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by mandoxv on 2009-02-08
I was installing Limewire and it while installing it froze so i cancelled it then i tried to install it again and that message showed up.

---

### Post by taurus on 2009-02-08
You probably still have dpkg or adept running in the background.  Look at the output of this command to see if there is one.

```
ps -A
```
Otherwise, just reboot.

---

### Post by mandoxv on 2009-02-08
im a noob in ubuntu lol sorry my friend told me i have to upgrade java but i have to do it manually which is difficult for me anyone know how?

---

### Post by mandoxv on 2009-02-08
I get this message now can anyone help?


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by oldos2er on 2009-02-08
> **mandoxv said:**
> I get this message now can anyone help?


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

 Run
```
sudo dpkg --configure -a
```
in a terminal.

---

### Post by mandoxv on 2009-02-09
Thanks a lot that made it work thanks again!

---

