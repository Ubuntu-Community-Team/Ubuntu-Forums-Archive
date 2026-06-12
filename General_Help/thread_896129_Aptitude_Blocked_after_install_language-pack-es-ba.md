---
title: "Aptitude Blocked after install language-pack-es-base"
date: 2008-08-20
forum: General Help
---

### Post by lelizondob on 2008-08-20
Hi, two days ago I installed the Spanish Language Support, via System -> Administration -> Language Support, the install proccess stopped at:

Setting up language-pack-es-base (1:7.10+20080205) ...
Generating locales...
  es_AR.UTF-8... 

After 6 hours of waiting I just decided to kill the process, but then I can't install anything via aptitude or apt-get. They both tell me to do:

dpkg --configure -a

After I do it, I get the same:

Setting up language-pack-es-base (1:7.10+20080205) ...
Generating locales...
  es_AR.UTF-8... 

I could just wait forever and it just won't finish, after waiting 8 hours I just decided to kill the process again and post here..

I've been searching for a solution but I couldn't find anything at all.

What can I do?

Thanks in advance

Luis

---

### Post by emvy on 2008-08-30
I have the same exact problem only for laguage-pack-en-base package
I tried to use 'sudo dpkg --configure -a' but it still stucks at the same point
I tried purging the language package but it stucked again "uninstalling lan..." dor long time and I closed it
plz help guys!

---

