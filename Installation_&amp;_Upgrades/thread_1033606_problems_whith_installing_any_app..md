---
title: "problems whith installing any app."
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by maboli on 2009-01-07
every thing was working perfectly whith ubuntu 8.10 then i tried to install limewire but i culdnt and this messege appear (only one software managment tool is allowed to run at the same time) and i am sure 100% that this was the only software running on my pc.
i tried the same thing several times i even tried closing my pc but nothing chenged.
i tried to add app. from APPLICATIONS>ADD\REMOVE
but this messege appeared(E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.)

i dont know hat to do i cant add any app. to my pc any more plzzzzz help me:confused:

---

### Post by oilchangeguy on 2009-01-07
from the terminal type sudo dpkg --configure -a and press enter.

---

### Post by maboli on 2009-01-08
i got this 


abdullah@abdullah-desktop:~$ sudo dpkg --configure -a
[sudo] password for abdullah: 
abdullah@abdullah-desktop:~$ sudo dpkg --configure -a
abdullah@abdullah-desktop:~$

---

### Post by sonu 1807 on 2009-01-08
it means you are done ... go ahead and install limewire

---

### Post by maboli on 2009-01-09
ive tried to add app. from add/remove application  it will just not respond!!!!

---

### Post by maboli on 2009-01-10
now whan i try to install codecs i got 



abdullah@abdullah-desktop:~$ sudo apt-get install gstreamer0.10-pitfdll
[sudo] password for abdullah: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
abdullah@abdullah-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

---

### Post by kranny on 2009-01-10
```
sudo dpkg --configure -a
```

---

