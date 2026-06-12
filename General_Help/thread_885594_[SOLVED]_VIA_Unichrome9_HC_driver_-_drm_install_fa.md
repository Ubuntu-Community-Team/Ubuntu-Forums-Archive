---
title: "[SOLVED] VIA Unichrome9 HC driver - drm install fails - for Ubuntu 8.04 LTS"
date: 2008-08-10
forum: General Help
---

### Post by _sluimers_ on 2008-08-10
I downloaded the driver from [http://linux.via.com.tw/support/downloadFiles.action]("http://linux.via.com.tw/support/downloadFiles.action"), installed it and now wonder what to do to get glxgears working?

glxgears is giving me the following error:
```
glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```


I tried installing drm to get rid of this, but it gives me the following error:
```

rogier@dhcppc3:~/drm/linux-core$ sudo make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
[sudo] password for rogier: 
make -C /lib/modules/2.6.22-14-generic/build  SUBDIRS=`/bin/pwd` DRMSRCDIR=`/bin/pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/rogier/drm/linux-core/drm_vm.o
/home/rogier/drm/linux-core/drm_vm.c:702: warning: &#8216;struct vm_fault&#8217; declared inside parameter list
/home/rogier/drm/linux-core/drm_vm.c:702: warning: its scope is only this definition or declaration, which is probably not what you want
/home/rogier/drm/linux-core/drm_vm.c: In function &#8216;drm_bo_vm_fault&#8217;:
/home/rogier/drm/linux-core/drm_vm.c:714: error: &#8216;VM_FAULT_NOPAGE&#8217; undeclared (first use in this function)
/home/rogier/drm/linux-core/drm_vm.c:714: error: (Each undeclared identifier is reported only once
/home/rogier/drm/linux-core/drm_vm.c:714: error: for each function it appears in.)
/home/rogier/drm/linux-core/drm_vm.c:760: error: dereferencing pointer to incomplete type
/home/rogier/drm/linux-core/drm_vm.c:782: error: dereferencing pointer to incomplete type
make[2]: *** [/home/rogier/drm/linux-core/drm_vm.o] Error 1
make[1]: *** [_module_/home/rogier/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
rogier@dhcppc3:~/drm/linux-core$ 

```

---

### Post by lennartack on 2008-08-10
The error glxgears gives you is because opengl is not installed. Install it by typing:
```
sudo apt-get install libgl1-mesa-glx
```

---

### Post by _sluimers_ on 2008-08-10
No, I have that installed, after a restart glxgears began working but glxinfo now crashes the computer, the screen goes black for a few seconds and then I'm back at the login screen. 

Another problem I encounter with Unichrome is the resolution. With openchrome I could take it to 1680x1050. Is that still possible with the Unichrome driver?

---

### Post by lennartack on 2008-08-10
about glxinfo: I have no idea what's wrong. You can read the output and possible error messages if you route output to a file:
```
glxinfo > file
```
And type cat file to read the contents after you logged in again ;)

Read this howto for more help with the resolution: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto). Ask any questions if you get stuck :)

---

### Post by _sluimers_ on 2008-08-11
This is what it gives me:

```

rogier@dhcppc3:~$ cat file
name of display: :0.0

```

And the fixvideoresolution page seems to be more for intel, ati and nvidia graphic chips, not via.

---

### Post by lennartack on 2008-08-12
Maybe that's because VIA chips work so great? :P

There are still some sections that apply to all chips on that page, like "Undetected Monitor Specs". Follow that one first. Since 3D is allready working, I think it doesn't have something to do with the chip/driver.

About the glxinfo: I have no idea what's wrong here. Am I the only one who answers this thread or something???

---

