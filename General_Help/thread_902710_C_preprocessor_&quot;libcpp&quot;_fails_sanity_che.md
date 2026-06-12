---
title: "C preprocessor &quot;/lib/cpp&quot; fails sanity check"
date: 2008-08-27
forum: General Help
---

### Post by _saiko on 2008-08-27
hardy in question...

getting that error when i try to compile something
seems i messed up something with the compilers
yes i have build-essential on, cpp/gcc/g++ ...
any clues?
i'd like to purge the whole build-essential pack, but then all dependancies want to get removed, any ways to completely purge only the compilers and reinstall them?

thanks

---

### Post by mali2297 on 2008-08-27
Does the error appear with just *some* thing that you try to compile? ...or is it anything?

---

### Post by _saiko on 2008-08-27
yes all it seems, everything i compile

---

### Post by mali2297 on 2008-08-27
Have you tried reinstalling just cpp?

---

### Post by _saiko on 2008-08-27
yes

---

### Post by _saiko on 2008-08-28
bump

---

### Post by _saiko on 2008-08-31
currently trying to completely remove (not just reinstall) all packages under build-essential

but the problem is... when i try to remove those 4: cpp cpp-4.2 gcc gcc-4.2
a great deal of packages lacks dependancy and automatically gets on the remove list too
is there a way to force only those packages i select to get removed temporarily?

---

### Post by _saiko on 2008-08-31
ok seems i resolved the issue

when i messed up the compilers it seems by that that i removed the features.h headers while installing a different package

the compilation goes fine now

---

### Post by Adam590 on 2008-10-02
I'm having the same exact issue. 
Please elaborate on the fix related to "features.h"?
Thanks


EDIT: 
Nevermind - reinstalling all the gcc files one by one did the trick. :)

---

