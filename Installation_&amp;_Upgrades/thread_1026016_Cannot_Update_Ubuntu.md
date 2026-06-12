---
title: "Cannot Update Ubuntu"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by fgerst on 2008-12-30
I have not been able to update. When I go to update, I cannot unselect SunJava. SunJava will not reinstall or update; when I go to accept the terms and conditions, I cannot select the box to agree and the package manager crashes. I have repeatedly attempted to completely remove the broken package, but I get an error message saying it could not remove it because it was in such an inconsistent state. Help!

---

### Post by taurus on 2008-12-30
Hit the Tab key to highlight the <OK> and Return key to accept it.

---

### Post by namdung on 2008-12-30
In terminal```

sudo apt-get update
```

If any error
```
sudo dpkg --configure -a
```

Now install sun-jre
```
sudo apt-get install sun-java6-jre
```

Remember to tick on agree option while installing.

---

