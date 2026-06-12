---
title: "Trouble Installing From Source"
date: 2005-11-07
forum: General Help
---

### Post by Revert on 2005-11-07
There're some programs I've been trying to install from source, and so far I've untarred them, then I cd to the directory, but every time I do ./configure I get the error "bash: ./configure: No such file or directory."

Example: on my Desktop's einstein-2.0-src.tar.gz.

eli@core:~/Desktop$ tar -xvzf einstein-2.0-src.tar.gz
(runs through untarring everything fine)
eli@core:~/Desktop$ cd einstein-2.0
eli@core:~/Desktop/einstein-2.0$ ./configure
bash: ./configure: No such file or directory

It seems like there's something real obvious I'm missing.  What're all the packages you need to do this (I'm pretty sure I have most of them, but I'm not positive)?  Can anyone help me with this? 

Thanks.

---

### Post by aysiu on 2005-11-07
```
sudo apt-get install build-essential
```

---

### Post by Revert on 2005-11-07
Already done, still getting the error.

---

### Post by aysiu on 2005-11-07
Maybe einstein doesn't have a configure script?

---

### Post by RAOF on 2005-11-07
Also, you may have to mark the configure script as executable.  Try "chmod +x configure"

---

### Post by Revert on 2005-11-07
/feels like a complete idiot.

No configure script. :???: 

Thank you for the prompt replies, sorry it was such a stupid question. :p

---

### Post by Arktis on 2005-11-07
Yes, there is no configure script. [http://games.flowix.com/en/](http://games.flowix.com/en/)
There is a makefile, though.  Try 'make' and then 'sudo make install' or 'sudo checkinstall', which will make and install a debian package you can easily remove or reinstall later if you want.  If it throws errors, then there are probably some packages you need to install first, and then try again.  To get it to make properly, I had to install libsdl-ttf2.0-dev, which installed about 10 other packages as dependancies.  I also had to install libsdl-mixer1.2-dev, which also needed 3 other packages as dependancies.```
sudo apt-get install libsdl-ttf2.0-dev libsdl-mixer1.2-dev
make
sudo checkinstall
```

---

### Post by Svip on 2005-11-07
This is one of the reasons I love the ls command. :)

---

