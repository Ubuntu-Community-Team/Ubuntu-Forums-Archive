---
title: "how to install gui on ubuntu server"
date: 2008-08-18
forum: General Help
---

### Post by taimur on 2008-08-18
hi
how to insatll gui on ubuntu server?

---

### Post by Iowan on 2008-08-18
Several ideas for you [here.]("http://ge.ubuntuforums.com/showthread.php?t=813698")  If you install one of the desktops, you'll get the extra "stuff" (dare I say, baggage?) like word processors, email, graphics, music player...

---

### Post by aysiu on 2008-08-18
Make sure you have the Universe repositories enabled (ask if you don't know how to do that), and then ```
sudo apt-get update
sudo apt-get install icewm xorg
startx
``` More details at [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Dr Small on 2008-08-18
Server's are built to run without a GUI. You shouldn't need a GUI if you are going to run a server, because generally, they will hog extra resources.

---

