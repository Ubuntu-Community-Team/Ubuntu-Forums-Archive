---
title: "ati drivers not working properly"
date: 2010-06-20
forum: Hardware
---

### Post by Chocrates on 2010-06-20
i -think- that my ati drivers aren't working properly.  I try to run warcraft3 with wine and get a disk not found error, which is due to an improperly configured driver according to the website. I also cant run glxinfo:
```
chris@bitey:~$ glxinfo
name of display: :1.0
Segmentation fault
chris@bitey:~$ sudo glxinfo
[sudo] password for chris: 
name of display: :1.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

a little background
in 9.10 the open source drivers worked fine.  I could play war3 and i could use the fglrx drivers without getting into trouble.
10.04 comes around and the whole mess with fglrx starts up.  Now that i dont need to develop with fglrx anymore i want to go back to the open source drivers so i can get some games to work again.
I have gone through the steps of forcefully purging fglrx from the system.  as for installing the open source ones all i could find to install was:
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
dpkg-reconfigure xserver-xorg
```

so i guess my question is, is my driver actually broken? and if it is, how can i fix it?

---

### Post by fendermon on 2010-06-20
Hi, 
Wish I could help. I have the fglrx driver running right in Lucid, no problems... but honestly gaming in Linux is just nuts. I've been trying to figure out how to run Far Cry for a month now...geeeez..I even have "Play on Linux" installed to make Wine manageable.   -Bill

---

