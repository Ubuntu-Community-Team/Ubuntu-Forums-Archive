---
title: "How to install video drivers."
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by sohaibma on 2007-02-03
I was on the Ubuntu Openchrome([https://help.ubuntu.com/community/OpenChrome#head-61015b8de079166a76899b391e1dca3f843fa11d](https://help.ubuntu.com/community/OpenChrome#head-61015b8de079166a76899b391e1dca3f843fa11d)) website for installing my Via VN800 drivers.

I got the 2D drivers right but the 3d driver installation process asks  me to enter this:
cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri login

where do i have to enter this? I tried it in terminal but it didnot recognize the CVS command
please help me out here. how do i make the 3d drivers work?

PS. I am using dapper

---

### Post by sohaibma on 2007-03-03
please ignore my first post.
I am trying to install the drivers in edgy from
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

when i reach the drm kernel modules section and try to execute the following command:
**make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via**

the following error shows up:
```
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/lib/modules/2.6.17-11-386/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-11-386/build'
make: *** [modules] Error 2

```

note: i have build-essential installed. The /build directory was not already there, i had to create it.

what is this error and how do i fix it.

---

