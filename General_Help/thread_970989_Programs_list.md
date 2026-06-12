---
title: "Programs list"
date: 2008-11-04
forum: General Help
---

### Post by Nabeel Ali on 2008-11-04
I want to create a list of installed programs in ubuntu?

---

### Post by _sAm_ on 2008-11-04
You will find a guide here;
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by Coreigh on 2008-11-04
EDIT: _sAm_'s answer above is much better than mine.

Are you looking for a listing of the packages installed on your computer? Or a listing of the programs that you would use on your computer?

In other words, programs that you use on your computer would be thing like calculator and word processor and Firefox. But packages are *everything* that makes Ubuntu run.

To get a list of _everything_
```
sudo dpkg -l > ./packageslist.txt
```
Type this in a terminal window and it will create a text file listing of ALL packages installed or partially installed.

I don't know an automated way to get a programs list but it is not that difficult to go through the Applications menu and write them down.

---

