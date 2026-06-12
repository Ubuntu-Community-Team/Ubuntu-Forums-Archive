---
title: "Need help fast: how do i install a tar.gz ??"
date: 2008-08-16
forum: General Help
---

### Post by Thyssenkrupp on 2008-08-16
Hey,

i have just downloaded 'frets on fire'

and it is in tar.gz form, how do i install it???

thanks!!

Jak

---

### Post by dje on 2008-08-16
in a terminal (applications >> accessories >> terminal):
```
sudo apt-get install fretsonfire-game
```
always search the repositories (synaptic, add/remove) for your program first ;) it's just easier that way :D

dje

---

### Post by Flyingjester on 2008-08-16
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by victor.zamanian on 2008-08-16
That particular tar archive contains the already compiled game, so all you have to do is just expand (or "extract") the contents of it and run the start script from your file browser if you can do that, or from the terminal:
```
$ /path/to/extract/dir/FretsOnFire
```
Note that if the /path/to/extract/dir/ is "." you must put ".":
```
$ ./FretsOnFire
```

If you wish to install the game, you can put the folder under /usr/local/ and then put a symbolic link (shortcut) in your /usr/local/bin/ folder so you can just run "FretsOnFire" in the terminal from anywhere.
```
$ sudo mv FretsOnFire/ /usr/local/
$ ln -s /usr/local/FretsOnFire/FretsOnFire /usr/local/bin/FretsOnFire
```
Best would of course be to install the game using aptitude/apt-get or download a .deb file from somewhere with the most current version, but if you always want to download the latest version from the site, you can do what I said above. :-) Hope this helps! Good luck!

---

