---
title: "Intel 945GME + 2.6.24 = No 3D"
date: 2008-04-25
forum: Hardware
---

### Post by DingoMD on 2008-04-25
After upgrading from 7.10 to 8.04:

```

dingo@laptop:/var/log$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Booting with the 2.6.22 kernel gives me "direct rendering: Yes", but no sound, so running it is not a solution.

Output of "compiz --replace", "glxinfo", "lspci", "xorg.conf" and "Xorg.0.log" on the attached file.

---

### Post by captainian on 2008-04-25
Might it have something to do with this?


[http://bugzilla.kernel.org/show_bug.cgi?id=10395#c4](http://bugzilla.kernel.org/show_bug.cgi?id=10395#c4)


The problem is reported to have been solved, but as a newbie I have no idea what to do in order to fix it. Wait for the new kernel to be automatically updated? Or apply the patch manually - if so, how to do it?

---

### Post by DingoMD on 2008-04-25
> **captainian said:**
> Might it have something to do with this?


[http://bugzilla.kernel.org/show_bug.cgi?id=10395#c4](http://bugzilla.kernel.org/show_bug.cgi?id=10395#c4)


The problem is reported to have been solved, but as a newbie I have no idea what to do in order to fix it. Wait for the new kernel to be automatically updated? Or apply the patch manually - if so, how to do it?

Thanks, that seems to be the problem. Unfortunately I'm a newbie too... Can someone help me fix this problem? :)

---

### Post by captainian on 2008-04-25
Yes, we need advice here.

If I understand coorectly, it should be fixed in 2.6.25.

Am I right?

[http://www.nabble.com/-PATCH--fix-IS_I9XX-macro-in-i915-DRM-driver-td16528420.html](http://www.nabble.com/-PATCH--fix-IS_I9XX-macro-in-i915-DRM-driver-td16528420.html)

---

### Post by DingoMD on 2008-04-25
I was thinking that maybe I could just recompile the DRM module. Would this work? On the other hand, I can't git it anyway ([http://gitweb.freedesktop.org/?p=mesa/drm.git;a=summary](http://gitweb.freedesktop.org/?p=mesa/drm.git;a=summary))
```

dingo@laptop:~$ git clone git://anongit.freedesktop.org/git/mesa/drm
Initialized empty Git repository in /home/dingo/drm/.git/
remote: Generating pack...
remote: Done counting 0 objects.
remote: aborting due to possible repository corruption on the remote side.
fatal: early EOF
fatal: index-pack failed
fetch-pack from 'git://anongit.freedesktop.org/git/mesa/drm' failed.

```

---

### Post by DingoMD on 2008-04-25
Sorry for double posting, but I got it working! :D

Here is how to do it:

Get necessary files:
```
sudo apt-get install git-core linux-headers-generic automake autoconf libtool
git clone git://anongit.freedesktop.org/git/mesa/drm
```

Compile and install libdrm:
```
cd drm
./autogen.sh --prefix=/usr
make
sudo make install
```

Compile and install DRM kernel module:
```
cd linux-core
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=i915
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
sudo depmod -ae
```

Reboot and enjoy! \\:D/

---

### Post by captainian on 2008-04-26
Thanks.

I'm probably an idiot, but I couldn't complete the second and third steps.

At "cd drm" it says no such file or directory. A file search gave me two drm folders, so I don't know which one I actually need.

Same with linux-core - no such file, and a file search came up with no results.

---

### Post by DingoMD on 2008-04-26
When you run "git clone git://anongit.freedesktop.org/git/mesa/drm" it should create the drm folder in your working directory (probably your home folder). linux-core is inside the drm folder. If you don't have those, maybe your git command did not succeed (look at my previous posts), if so, just try again later.

---

### Post by captainian on 2008-04-26
Thanks! Works like a charm now!

---

### Post by andy789 on 2008-04-30
Great post worked like a charm... Thank you !!

:guitar:

---

### Post by y2kprawn on 2008-05-10
fantastic, was trying to run torcs in more than 1 fps and this worked a charm. 

Question, will this effect my battery life when I dont have the machine plugged in ? Its a HP530 laptop . Is there any other thing I should know ?

---

### Post by y2kprawn on 2008-05-12
> **DingoMD said:**
> Sorry for double posting, but I got it working! :D

Here is how to do it:

Get necessary files:
```
sudo apt-get install git-core linux-headers-generic automake autoconf libtool
git clone git://anongit.freedesktop.org/git/mesa/drm
```Compile and install libdrm:
[code]

I am behind a proxy that blocks ports , cheers wondrous world of Irish internet. Git cannot get the required files as there is a port number involved. Is there any way of getting the DRM folder without using the GIT command line tool ?

---

### Post by zhuomingliang on 2008-06-01
I got the same problem, and fix it now. thanks.

---

### Post by Leech333 on 2008-07-11
i've done all the steps without any problems/errors. but no effect at all.
glxinfo says
> 
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


my notebook is HP Pavilion dv6000, Intel Corporation Mobile GM965/GL960
any suggestions?

---

### Post by Leech333 on 2008-07-11
:confused:

---

### Post by fishMD on 2009-04-27
same problem with 2.6.27-11, I try fix but at this step:
> **DingoMD said:**
> 
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=i915

fail:
> fishmd@fishmd-ubuntu:~/drm/linux-core$ make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=i915
make -C /lib/modules/2.6.27-11-generic/build  SUBDIRS=`/bin/pwd` DRMSRCDIR=`/bin/pwd` modules
make: *** /lib/modules/2.6.27-11-generic/build: No such file or directory.  &#1047;&#1091;&#1087;&#1080;&#1085;&#1082;&#1072;(stop).
make: *** [modules] &#1055;&#1086;&#1084;&#1080;&#1083;&#1082;&#1072;(error) 2plz help :confused:

---

