---
title: "HOW-TO preserve installed packages between multiple debian computers"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by nick_ninja on 2009-03-24
If you're reading this, you are probably migrating or thinking about migrating to a new computer. This method, as the title suggests, preserves installed packages between multiple computers, allowing you to (a) upgrade more easily and (b) save space on backups. This does, however, require perl, so make sure you've got that first. You can use any folder you'd like, but I will assume you are using your home folder.

Run this command:
```
dpkg -l|egrep ^ii|perl -e 'print "#!/bin/bash\n";while(<STDIN>){$_=~ m/ii *(\S*)/;print "apt-get install $1\n";}'>~/pklist.sh
```

**Conclusion**
pklist.sh now contains a shell script that when transferred to a new computer and run as root, will reinstall everything.

Note: If you have removed packages that come with ubuntu by default, your new computer will not reflect those changes. Sorry! :(

-Nick_Ninja

---

