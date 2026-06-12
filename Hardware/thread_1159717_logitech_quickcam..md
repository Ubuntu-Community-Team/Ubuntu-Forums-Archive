---
title: "logitech quickcam."
date: 2009-05-14
forum: Hardware
---

### Post by greythorne on 2009-05-14
I am trying to install logitech quickcam pro 5000 and want to use it for skype and others.

this is what i did:
```
$ **svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk**

 $ **cd trunk**

 $ **make**

 $ **sudo make install**
```but when doing make got this:
```
amin@darkstar:~/trunk$ make
-------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to http://linuxtv.org/.
 Using the Berlios SVN repository is now deprecated.
 Please check http://linux-uvc.berlios.de/ for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------
amin@darkstar:~/trunk$ make uvcvideo
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/amin/trunk/uvc_driver.o
  CC [M]  /home/amin/trunk/uvc_queue.o
  CC [M]  /home/amin/trunk/uvc_v4l2.o
/home/amin/trunk/uvc_v4l2.c: In function ‘uvc_v4l2_do_ioctl’:
/home/amin/trunk/uvc_v4l2.c:986: warning: passing argument 1 of ‘v4l_compat_translate_ioctl’ from incompatible pointer type
/home/amin/trunk/uvc_v4l2.c:986: warning: passing argument 2 of ‘v4l_compat_translate_ioctl’ makes integer from pointer without a cast
/home/amin/trunk/uvc_v4l2.c:986: warning: passing argument 3 of ‘v4l_compat_translate_ioctl’ makes pointer from integer without a cast
/home/amin/trunk/uvc_v4l2.c:986: error: too many arguments to function ‘v4l_compat_translate_ioctl’
make[2]: *** [/home/amin/trunk/uvc_v4l2.o] Error 1
make[1]: *** [_module_/home/amin/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [uvcvideo] Error 2
amin@darkstar:~/trunk$ 

```any ideas what could be wrong here??

Thanks.

---

### Post by astarr on 2009-08-08
Having the same problem.
This seems to be a little bit helpful, and I'm trying to work through it:
[http://ubuntuforums.org/showthread.php?t=838210]("http://ubuntuforums.org/showthread.php?t=838210")
I'll post after trying and if I figured it out.

Best of luck!

Edit: I think there might be a directory problem with Error 2, as your _module_ shouldn't contain your home folder.

---

### Post by autumnraine on 2009-09-24
Has anyone found a solution to this, or know of another way to get this configured? Any help would be appreciated.

---

