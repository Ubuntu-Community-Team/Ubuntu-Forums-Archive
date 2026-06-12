---
title: "Synaptic Not Working"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by dhtml12345 on 2009-09-16
I've tried to install OpenGL GLUT via Synaptic Package Manager and Terminal (the specific package is "freeglut3-dev"), but some of the necessary files can't be downloaded because of a 404 Not Found error.  How can I fix this problem or how can I download the installation files manually?

Thank you very much for any help, advice, or direction.  I need GLUT for a Computer Science class.  I'm not a Linux expert.

Below is the Terminal output from my attempts:

```
donnie@donnie-laptop:~$ sudo apt-get install freeglut3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following extra packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev mesa-common-dev xlibmesa-gl-dev
The following NEW packages will be installed:
  freeglut3-dev libgl1-mesa-dev libglu1-mesa-dev mesa-common-dev
  xlibmesa-gl-dev
0 upgraded, 5 newly installed, 0 to remove and 5 not upgraded.
Need to get 431kB/588kB of archives.
After this operation, 2617kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Err http://us.archive.ubuntu.com jaunty-updates/main mesa-common-dev 7.4-0ubuntu3.1
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com jaunty-updates/main libgl1-mesa-dev 7.4-0ubuntu3.1
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com jaunty-updates/main libglu1-mesa-dev 7.4-0ubuntu3.1
  404 Not Found [IP: 91.189.88.46 80]

Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-common-dev_7.4-0ubuntu3.1_all.deb  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_7.4-0ubuntu3.1_all.deb  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa-dev_7.4-0ubuntu3.1_i386.deb  404 Not Found [IP: 91.189.88.46 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by ubongo2008 on 2009-09-16
sometimes packages are updated ... try apt-get update
or try an other country mirror for example 
[http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) .....

---

### Post by dhtml12345 on 2009-09-16
Updating worked!

Thanks for your quick reply.

---

