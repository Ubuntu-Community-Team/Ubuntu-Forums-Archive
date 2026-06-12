---
title: "NVidia 7900 hangs up the computer"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by bff7755a on 2008-03-25
Hello.

I booght a new machine - MB Asus P5K Pro, Intel c2duo; With the previous MB everything were OK. But when I installed the old video card (NVidia GeForce 7900) on new MB, my system hangs up in random time.
I turned off compiz first of all, and I have more stability. But sometimes it hangs :(

Please, tell how can I solve this problem. I has drivers from repository (I have Ubuntu 7.10) - 104.xx.xx (I know the last is 169.12) :confused:

---

### Post by Vermind on 2008-03-25
Hello.
First of all, I am using official NVIDIA drivers downloaded from their site, installed manually.
I never had a problem with crashing with their drivers. The procedure is to go to the
[nvidia site]("http://www.nvidia.com/page/home.html")
and click download drivers, then choose geforce something less than 9 and search. If You agree with the nvidia license, then download the installer.
it needs to be run outside X. I usually quit my session, go to a terminal ( ctrl-alt-F2 ), the default graphical desktop is either ctrl-alt-F7 or ctrl-alt-F9.
and login using my user name and password. 
I then kill the login manager: ```
sudo killall -s TERM gdm
``` in order to stop X.
If You use restricted drivers, You should also unmount the directory overlay for them, otherwise the nvidia driver will be lost on next reboot: ( sudo umount /lib/modules/`uname -r`/volatile )
Then I go to my Desktop where I downloaded the installer ( cd Desktop )
set the installer executable ( chmod 750 NVIDIA-* )
and run it as super user ( sudo ./NVIDIA-* -a -n )
it asks  whether to update Your old driver ( yes ) and whether to download an updated installer ( no ). In the end, it asks whether to update Your xorg.conf. This is Your choice; if You already use an nvidia driver and compiz works for You, no need to.
If the installer is unable to compile the driver, You must install build tools ( sudo aptitude install build-essential )
when the installer completes, run 
```
sudo gdm 
``` to start the session manager again. You now have new drivers.

---

### Post by bff7755a on 2008-03-27
Thank you. I've tried to do so but something bad happened :(.

```
mutex@desktop:~$ glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```
I have this after install 169.12 drivers. My current screen resolution is only 640x480 :((

---

### Post by Vermind on 2008-03-28
Hello,
it looks like the nvidia driver could not be loaded.
I just remembered: The Ubuntu nvidia driver uses an install command that does not apply for the official one. In order to use the official one, You have to edit two files. First file:
```
sudo nano -w /etc/modprobe.d/lrm-video
```
Comment out the line that says ```
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
```
so it becomes ```
#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
```.
press ctrl-x to exit, y and enter to save.

Second file:
```
sudo nano -w /etc/default/linux-restricted-modules-common
```
change the last ```
DISABLED_MODULES=""
``` to ```
DISABLED_MODULES="nv nvidia_new"
```. This prevents Ubuntu from using their nvidia driver instead of the official one. Change these back if You wish to go back to the Ubuntu one.

Then reinstall nvidia driver as before:
```
#kill X
sudo killall -s TERM gdm Xorg
sudo umount /lib/modules/`uname -r`/volatile
cd $HOME/Desktop
chmod 750 NVIDIA-*
sudo ./NVIDIA-* -a -n
#answer yes to update old driver, no to xorg.conf change
#restart X
sudo gdm
```

If this does not help You could post Your xorg.conf, Your /var/log/Xorg.0.log (or /var/log/Xorg.1.log if the failsafe session with this small resolution starts) and I could try to see what is wrong.

---

