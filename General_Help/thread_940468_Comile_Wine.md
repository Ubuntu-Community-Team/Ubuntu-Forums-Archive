---
title: "Comile Wine"
date: 2008-10-07
forum: General Help
---

### Post by Sanix on 2008-10-07
I tried to compile Wine but when I executed the ./configure command, I got the following warning 
configure: WARNING: No OpenGL library found on this system.
Wine will be build without OpenGL or Direct3D support.

I tried to download all possible opengl libraries but obviously the wrong ones. Which one, do I need to download for Ubuntu? Do you know, if there are any precompiled wine builds for 0.9.45, since it's nearly impossobile to compile it (I got so many errors, with not solutions in the internet, even people buying Cedega because of it).

---

### Post by justleen on 2008-10-07
any specific reason your not installing the latest version from the repositories?

And if you compile it from source, you'll have to add extra flags to the ./configure stating where it can find the libraries, its probably looking for it in a location which doenst contain the libs..

---

### Post by geirha on 2008-10-07
```
sudo apt-get build-dep wine
``` should install the necessary packages to build the version of wine which is in your repositories. The build dependancies are probably the same for the version you're attempting to build.

---

