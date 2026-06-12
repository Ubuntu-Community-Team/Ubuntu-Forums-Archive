---
title: "strange problem with apt"
date: 2008-07-13
forum: General Help
---

### Post by go_beep_yourself on 2008-07-13
Anybody know what's going on here?

```
root@ubuntu:~# dpkg -l | grep nvidia
rc  nvidia-glx-new                             169.12+2.6.24.13-19.44             NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                  NVIDIA binary kernel module common files
ii  nvidia-settings                            1.0+20080304-0ubuntu1.1            Tool of configuring the NVIDIA graphics driv
root@ubuntu:~# apt-get --purge remove nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 78 not upgraded.
root@ubuntu:~# 
```

---

### Post by sayakb on 2008-07-13
Do this as sudo. Also, does this package show up as installed in Synaptic?

---

