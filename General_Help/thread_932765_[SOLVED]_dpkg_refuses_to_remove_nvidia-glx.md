---
title: "[SOLVED] dpkg refuses to remove nvidia-glx"
date: 2008-09-28
forum: General Help
---

### Post by ShadowWraith on 2008-09-28
When I try to remove the package nvidia-glx using any utility, I receive this message:
(Reading database ... 253160 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/X11R6/lib/modules/extensions/libglx.a': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx

Please help, this is preventing me from installing my video card drivers!

---

### Post by mikewhatever on 2008-09-28
Can you post the output of the following:
> dpkg -s nvidia-glx

Also, elaborating a bit might help. The package you are trying to remove is a video driver, so why remove it if you want to install one.

---

### Post by ShadowWraith on 2008-09-28
The nvidia-glx package is a leftover from my old version of ubuntu. When I upgraded to 8.04, the packages attempted to purge and replace to nvidia-glx-new, but this one was left. At that point, I was running a Geforce 4 mx 440. I somehow managed to get around the fact that nvidia-glx wouldn't install by running envyng -t. Now, I've "upgraded" to a geforce 6200 le, and the drivers flopped.  I can't get around it with envyng, and I can't uninstall nvidia-glx, which prevents me from manually installing the drivers.

---

### Post by phidia on 2008-09-28
You can try "sudo nvidia-installer --uninstall" There is a method for removing all previous nvidia drivers,but I'm not being to successful searching it tonight. 

Take a look at the guide [here]("http://ubuntuforums.org/showthread.php?t=797270&highlight=remove+nvidia") and specifically the means of removing previous drivers-hope that helps.

---

### Post by ShadowWraith on 2008-09-28
Package: nvidia-glx
Status: deinstall ok half-installed
Priority: optional
Section: restricted/misc
Installed-Size: 12040
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.24 (2.6.24.13-19.45)
Version: 1:96.43.05+2.6.24.13-19.45
Config-Version: 1:96.43.05+2.6.24.13-19.45
Replaces: nvidia-glx-src
Provides: xserver-xorg-video-2
Depends: libc6 (>= 2.1), libgl1-mesa | libgl1, libglu1-mesa | libglu1, libx11-6, libxext6, linux-restricted-modules-common, xserver-xorg-core (>= 1:0.99.0-1)
Suggests: nvidia-kernel-source (>= 96.43.05), nvidia-settings
Conflicts: nvidia-glx-legacy, nvidia-glx-new, nvidia-glx-src, nvidia-xconfig
Description: NVIDIA binary XFree86 4.x/X.Org driver
 These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
 of OpenGL applications via a direct-rendering X Server and support the newer
 GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
 flat panel displays are also supported.
 .
 If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
 package instead of this one

That's the output
Please help!

---

### Post by ShadowWraith on 2008-09-28
Before anyone suggests it, this is what forcing gets me:

???@???:~$ sudo dpkg --remove --force-remove-reinstreq nvidia-glx
[sudo] password for david: 
(Reading database ... 253153 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/X11R6/lib/modules/extensions/libglx.a': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx

---

### Post by mikewhatever on 2008-09-29
Have you tried reinstalling nvidia-glx? Perhaps if fully installed, it can also be successfully removed.

---

### Post by drs305 on 2008-09-29
I use EnvyNG to install my nvidia drivers. During the install, the old drivers have to be uninstalled. If you watch the commands as they execute inside EnvyNG you will see it uninstall the old ones before installing the newer ones.

You may want to try EnvyNG and see if it will do things for you automatically, including removing the old drivers. To install EnvyNG:
```
sudo apt-get install envyng-gtk
```

Once installed, it is accessed via System Tools.

---

### Post by ShadowWraith on 2008-11-03
I got past this problem by creating the problematic directory. EnvyNG did not work.

---

