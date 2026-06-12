---
title: "Problem installing Java 6"
date: 2008-09-12
forum: General Help
---

### Post by Crowder on 2008-09-12
Hey guys, first post, new to the os... i'll try not to look stupid lol 

Anyway, I was in the terminal window trying to install java 6
("sudo apt-get install sun-java6-jdk")

...the installation went pretty smoothly, but i somehow got stuck on the license agreement screen. I just ended it, and now I get the following message if I try to resume or open the package manager:
  
   "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' 
    to  correct the problem. 
    E: _cache->open() failed, please report."

If I then try to enter said command into the terminal, I am told that I need superuser privileges (i.e. "dpkg: requested operation requires superuser privilege")

Thanks in advance for any help you can provide.

P.S. I apparently can't use the package manager until this is fixed.

---

### Post by Crowder on 2008-09-12
nevermind, found what i needed in another thread, just forgot to sudo.
 
[http://ubuntuforums.org/showthread.php?t=127148]("http://ubuntuforums.org/showthread.php?t=127148")

Thanks anyway!

---

