---
title: "Trying to install...."
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by dmdyne on 2009-03-01
Any time I try to install Flash or OpenJDK or any additional items, I keep getting the same error.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What do I need to do? When I try to type that line in the terminal window it says I need superuser privledges. I only have 1 user on here so far and I'm the admin....

I am definatly new to Ubuntu so...try to be specific. lol

---

### Post by ibutho on 2009-03-01
Run Applications -> Accessories -> Terminal and enter
```
sudo dpkg --configure -a
```

---

