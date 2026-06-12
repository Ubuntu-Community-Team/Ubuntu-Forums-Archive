---
title: "X  Messed Up"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by asimon623 on 2005-09-07
I was trying to get ssh to work with x so i tried some different x server installs and now my desktop wont start up normally, I end up in like a black screen where I can do terminal stuff. How can I revert back to the default x settings without reinstalling the OS?

Thanks

---

### Post by mlomker on 2005-09-07
Honestly, a reinstall might be the rational decision...you might not ever figure out which files were overwritten.  Are you getting any useful error messages on the screen? 

You could look at the contents of /var/log/Xorg.0.log for clues.

---

### Post by amohanty on 2005-09-07
sudo apt-get remove xserver-xorg
sudo apt get install xserver-xorg

theres a possibility you may not be able to remove it because of ubuntu-desktop package's dependency on it.

In that case you can try to reinstall the entire ubuntu-desktop package:
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

HTH
AM

---

