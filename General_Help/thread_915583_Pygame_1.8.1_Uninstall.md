---
title: "Pygame 1.8.1 Uninstall"
date: 2008-09-10
forum: General Help
---

### Post by Perk on 2008-09-10
I compiled and installed from source, but how do I uninstall it? I don't see it in Add/Remove Programs or in Synaptic. I don't see any uninstall.py files either. I'm using Ubuntu 8.04.

---

### Post by unutbu on 2008-09-10
If the source README or INSTALL file does not include instructions on how to uninstall, perhaps try this trick:
```

sudo apt-get install checkinstall
sudo checkinstall --fstrans=no -D install.py
```

Change "install.py" to the correct install command if need be.
The above commands will create a .deb package instead of installing pygame.

Now to uninstall pygame we install the .deb, and then uninstall it:
```

sudo dpkg -i pygame.deb
sudo dpkg -r pygame

```
See 
[http://www.asic-linux.com.mx/~izto/checkinstall/](http://www.asic-linux.com.mx/~izto/checkinstall/)
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
for more info on checkinstall.

---

### Post by cariboo on 2008-09-10
If you still have the directory with the source code in it you can try:

```
sudo make uninstall
```

Jim

---

