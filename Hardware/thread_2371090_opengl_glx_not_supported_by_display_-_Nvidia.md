---
title: "opengl glx not supported by display - Nvidia"
date: 2017-09-10
forum: Hardware
---

### Post by seninnte on 2017-09-10
I ask for help. I can not solve the problem for a week.

I have the Nvidia 730M and the integrated video in the i7 3630qm.
System: ubuntu 16.04 assembled from minimal cd.
Installed an openbox, without dm. The box is launched from:
> cat .bash_profile
startx

When you run the steam, it says:
> opengl glx not supported by display

The  drivers are the last, installed as well as the prime via > apt install  -no-install-recommends nvidia-384 nvidia-settings nvidia-prime from ppa At boot time, prime requires lightdm, which I will not exactly put.

> nvidia-settings


[INDENT]ERROR: Error querying enabled displays on GPU 0 (Missing Extension).

ERROR: Error querying connected displays on GPU 0 (Missing Extension).

 Message: PRIME: No offloading required. Abort
 Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.[/INDENT]
[INDENT]
[/INDENT]
> 
lspci
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 730M] (rev a1)


> lrwxrwxrwx 1 root root      45 Sep  4 22:01 nvidia_drv.so -> /etc/alternatives/x86_64-linux-gnu_nvidia_drv
ls: cannot access '/usr/lib/xorg/modules/updates/drivers/': No such file or directory

> glxgears
Error: couldn't get an RGB, Double-buffered visual

---

### Post by seninnte on 2017-09-12
New info.
> 

/usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch

(EE)
Fatal server error:
(EE) Server is already active for display 0
   If this server is no longer running, remove /tmp/.X0-lock
   and start again.
(EE)
(EE)
Please consult the The X.Org Foundation support
    at [http://wiki.x.org](http://wiki.x.org)
 for help.
(EE)
Aborted (core dumped)



First did xclock and immediately DISPLAY = 0.0 xclock - nothing happened.
Then just executed DISPLAY = 0.0 xclock and in response to the error: Can not open display: 0.0

> root@temp:~# xclock
DISPLAY=0.0 xclock

root@temp:~# DISPLAY=0.0 xclock
Error: Can't open display: 0.0


> root@temp:~# ls -dl /etc/
drwxr-xr-x 117 root root 4096 Sep 11 23:34 /etc/

---

### Post by efflandt on 2017-09-14
The normal default X DISPLAY is :0
But if running anything from a terminal window, you should not have to specify that.

Normally when not running as root, nvidia drivers would be installed using:```
sudo apt install nvidia-384
```Which would automatically include nvidia-prime, nvidia-settings, and nvidia-opencl-icd.

Does glxinfo succeed or fail?

What shows for graphics drivers being used in output of (does the Intel graphics show up as well): lspci -v

My gaming laptop no longer functions, but when it did, lspci listed the Intel graphics as "VGA" and my GTX 765M as "3D" instead. Does your laptop have any visual indication of which graphics is being used? The power LED on my laptop was blue when Intel graphics was active, and amber when Nvidia was active.

---

