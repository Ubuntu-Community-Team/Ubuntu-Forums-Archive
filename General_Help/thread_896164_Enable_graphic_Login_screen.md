---
title: "Enable graphic Login screen"
date: 2008-08-20
forum: General Help
---

### Post by TTTamer on 2008-08-20
Hi all, 

My bad, i disable some graphic login at Gnome`s System menu and now i can`t revert the choice. I was using Ubuntu 8 and wen clicked to disable the graphic login, it becomes black..  hope any one can help me to revert it from command line... 

Tamer.

---

### Post by Vivaldi Gloria on 2008-08-20
In terminal give the commands:

```

sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
```

and restart using the command

```
sudo reboot
```

---

### Post by tuxxy on 2008-08-20
Do you mean login and start GNOME? 

type this to launch the GUI.

```
startx
```

---

### Post by TTTamer on 2008-08-20
Just a second ...

---

### Post by TTTamer on 2008-08-20
thanks a lot!!!

Vivaldi Gloria, perfect solution! 

tuxxy, worked, i didn't know this command... 

thanks a lot guys!!!

---

### Post by X4320 on 2008-09-15
had the same problem today.
thought a different way about that option

(( newcomer here aswell ))

first search - first click - first solution - WORKS
thanks guys :D

---

