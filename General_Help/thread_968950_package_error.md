---
title: "package error"
date: 2008-11-03
forum: General Help
---

### Post by heman22union on 2008-11-03
I'm having trouble installing packages.... I"m on Kubuntu 8.4 and kde4 and the package manager I'm using is synaptic package manager. I select packages to install and hit apply, it downloads them, and installs them.... and then at about 100% finished it just sit there for a long time and does nothing.... here is a screen shot...

[IMG]http://i292.photobucket.com/albums/mm17/heman22union/Ubuntu/bugerror5.jpg[/IMG]

i had the same problem when installing python packages... it installed things and then ended up sitting there and doesn't do anything.

i also have successfully installed games between the current mess up and the python mess up...

---

### Post by scragar on 2008-11-03
ldconfig takes a long time to complete since it rebuilds a list of the libraries available on your system, just let it run for a while(Normaly while it is running your HD activity light will flash, so use that as a clue as to the fact that it's not stopped, it's just taking a while).

---

### Post by heman22union on 2008-11-03
how long are we talking about it taking? because it has been there for at least 30 minutes...

---

### Post by scragar on 2008-11-03
oh, 30 minutes does sound like it has definatly frozen, kill it off, you will need root perms to do so if I'm not mistaken, so from a terminal run:
```
sudo killall synaptic
```
Then when it closes of you might need to run the process yourself:
```
sudo ldconfig
```

If it complains next time you do to run synaptic that you need to run **dpkg-reconfigure -a** then open a terminal and run```
sudo dpkg-reconfigure -a
```although I can't imagine that this will be likely.

---

