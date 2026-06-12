---
title: "Synaptic wants to remove my packages"
date: 2005-11-19
forum: General Help
---

### Post by yaztromo on 2005-11-19
I installed libmac2, monkeys-audio and xmms-mac. Unfortunately I had to do a dpkg --force-all to make this work because they depend on libstdc4.0.2 and only 4.0.1 is available in the repository.

Anyway monkeys audio works quite happily.

Now synaptic won't let me install anything without uninstalling these "broken" packages first. Is there anyway to stop this?

Help appreciated.

---

### Post by manicka on 2005-11-19
Not sure if this will stop it

Package-->Lock Version

---

### Post by yaztromo on 2005-11-19
Thanks for the lightning reply.

Tried your suggestion but no luck.

---

### Post by yaztromo on 2005-11-19
Futhermore I read this in the synaptic help file 

"Synaptic Package Manager will not allow any further changes to the system before all broken packages are fixed."

I hope there is a way to override this.

---

### Post by manicka on 2005-11-19
A really crude way I've done before is to look at the properties of the package (right click-->properties) and find where all it's files are installed. Copy them, remove the package then copy them back.

It's not pretty and I wouldn't really recommend it, but I did do it many moons ago in SuSE to get some printer drivers installed.

---

### Post by teaker1s on 2005-11-19
there are various tools for examining packages and adding files could you simply rename it? or copy it's contents and create a new package with the higher version number

---

### Post by gnumerouno on 2005-11-21
I installed Monkey's Audio from source like in this thread
[http://ubuntuforums.org/showthread.php?t=30788&highlight=monkey%27s+audio]("http://ubuntuforums.org/showthread.php?t=30788&highlight=monkey%27s+audio")
and then used this to convert to flac
[http://ubuntuforums.org/showthread.php?t=82806&highlight=monkey%27s+audio]("http://ubuntuforums.org/showthread.php?t=82806&highlight=monkey%27s+audio")

I would suggest you install checkinstall, and do ```
sudo checkinstall
``` instead of ```
sudo make install
``` to create a .deb package you can uninstall, if need be.

---

