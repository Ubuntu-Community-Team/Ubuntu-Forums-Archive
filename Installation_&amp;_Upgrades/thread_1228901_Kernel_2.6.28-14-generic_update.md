---
title: "Kernel 2.6.28-14-generic update"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by Sooda on 2009-08-01
First it broke NVIDIA graphics as usual which I have been unable to fix. I suspect my kernel update was partial because there was problem with missing *linux*-*restricted*-*modules* (*2.6.28-14.19*) headers.

I have uninstalled NVIDIA 185.18.31, reinstalled without success, while installing manualy driver libglx.so.xserver-xorg-core problems occured (mainly invalid link/ can't find).

Ubuntu updates can be really frustrating, how I can reinstall kernel 2.6.28-14-generic to ensure it gets fully installed (perhaps link to kernel install)?

How to remove NVIDIA default install?

How to stop gdm once and for all? Using 'sudo /etc/init.d/gdm stop' might tell gdm is stopped while in other displays (how to call them, sessions?) like Crtl+Alt+F7 you are asked 'Would you like to try different display (Range 0 to 7)' or similar.

Obviously there is kernel and NVIDIA conflict.

---

### Post by mikewhatever on 2009-08-01
Both linux-headers-2.6.28-14-generic and linux-restricted-modules-2.6.28-14-generic are in the repositories, just verify that they are installed. Ubuntu has the following metapackages installed by default, to make sure the corresponding packages are the latest version:
linux-image-generic
linux-restricted-modules-generic
linux-headers-generic

Make sure all three are installed to avoid future confusions. Also make sure dkms (Dynamic Kernel Module Support Framework) package is installed.
All the above are installed by default and should get you safely over kernel updates.

What is the default Nvidia installation? Last time I checked Nvidia drivers were not installed by default.

If /stc/init.d/gdm stop doesn't work as expected, use the recovery mode. You'll never have to stop xserver again, since it doesn't get started in the first place.

---

### Post by Soul-Sing on 2009-08-01
Prob. a conflict between "self updated" nvidia drivers and the newest -14 kernel update/grade
The -13 kernel is working allright?

---

### Post by TheVirtualn on 2009-08-01
Yes, the kernel 2.6.28-13 works right.
To solve the problem, you must to go at the [www.nvidia.com](www.nvidia.com), and download the last driver for your card.

Enjoy

---

### Post by Sooda on 2009-08-01
@ [mikewhatever]("http://ubuntuforums.org/member.php?u=160645") checked with Synaptic Quick Search, all needed things listed in your post were installed, even dkms.

Got it all working again, solution is surprisingly simple.

First of previous NVIDIA drivers need to be uninstalled. Then you can Use System > Administration > Hardware Drivers to activate recommended NVIDIA driver (downloads and installs automatically), restart is reuqired after that. Now everything should work properly.

Manual NVIDIA driver instalation is bad (going to command line mode, stopping gdm and then running driver file, afterwards starting gdm again). Each kernel update, which happens pretty often, changes core things while breaking manually set up graphics driver settings. It is supposed to work like that. When you let Ubuntu take care of video driver trough Hardware Drivers future kernel updates go smoothly without breaking graphics settings.

I write step by step guide how I got it working again. My computer name is 'tonis' (without ''). You need to replace it with your computer name. Best is to write these steps on paper, then you can try them out.

Going to "command line" version of Ubuntu Ctrl+Alt+F1. You might need to log in -- enter your user name and password after that. Then stopping gdm (if you got kdm command differs and I do not know it):
```
sudo /etc/init.d/gdm stop
```This should in theory shut down gdm at once, but with this 'many windows' style hit Ctrl+Alt+F7 (or other F2 to F12) to see are these windows also in command line mode, maybe you have to answer some questions, but try to get these to into text mode (or something which seems like text mode).
You can try:
```
sudo /etc/init.d/gdm stop
```command more in Ctrl+Alt+F1 window, when you are at last in command line mode we can continue.

First I changed directory to folder where all my NVIDIA *.run files where (these which you get from NVIDIA drivers site). In my case it was on desktop:
```
cd /home/tonis/Töölaud
```Töölaud means in Estonian Desktop.
uninstalling is similar to installing, only in the end ' --uninstall' gets added:
```
sudo sh N
```now is good time to press TAB key on keybaord, it will try to type most of matching file name, still you need to finish it if there are many similar file names (NVIDIA driver version files in our case):
```
sudo sh NVIDIA-Linux-x86-185.18.31-pkg1.run --uninstall
```I am not used to it, for my surprise it actually uninstalls, I do not know why 'sh' needs to be there, but it works that way. File name can vary in your case.

It should tell driver is uninstalled, when you have tried to install many driver versions try to remove them same way (just to be sure, though latest install should remove previous install anyway).

Now we can start gdm again:
```
sudo /etc/init.d/gdm start
```Graphical Log In screen should appear, now you can go to System > Administration > Hardware Drivers and activate suggested (or listed) NVIDIA graphics driver which you like. Restart is required after downlaod and instalation.

I know we got perfectly fine NVIDIA *.run files downloaded already, but letting Ubuntu get right one from internet is worth it.

When you have messed with command line and driver installation before it should not be so difficult to do.

With automatically installed NVIDIA driver I swapped from 2.6.28-13-generic to 2.6.28-14-generic kernel without any problem.

---

### Post by UltraZone on 2009-08-01
I have tried this already, and the Hardware Drivers install the NVIDIA 180.xx drivers, even after intalling that Compiz does not work for me.  Does it work for you?

---

### Post by Sooda on 2009-08-01
I do not use Compiz, I use minimal effects. This uninstall and Hardware drivers did the trick for me. What you have tried so far and what not? Kernel update also messed up your graphics driver install?

---

### Post by UltraZone on 2009-08-01
Before the kernel update the Nvidia 185.xx drivers were working smoothly.  I downloaded the *.run drivers directly from Nvidia and it worked, however the *.14 kernel somehow broke them and it reverted to the base Ubuntu-supported drivers.  Again the 180.xx drivers do install, but they do not enable Compiz to work.  Anyone knows why the 185 or 190 drivers do not appear as a choice in the Hardware Drivers list?

---

### Post by Sooda on 2009-08-02
I think these driver versions are too new, they have not been Ubuntufied yet. Maybe I should had mentioned before but I got Ubuntu 9.04 -Jaunty Jackalope. You have to edit your Synaptic options, then it will list newest things (I have forgotten how). They are not listed for reason, they are mostly experimental. Though you know 185 works fine, change Synaptic list? settings and download newest.

I think I maybe did restart to computer after I had uninstalled NVIDIA driver. Try disabling all drivers from Hardware Drivers, restart computer (it should load in low graphics mode or use Ubuntus defaults) try installing from Hardware manager again (maybe you can only activate it and restart computer). Which video card you got?

EDIT:

Read this blog, pretty same problem: [http://www.lauracowen.co.uk/blog/2008/11/30/updating-nvidia-graphics-drivers-with-ubuntu-kernel-updates/](http://www.lauracowen.co.uk/blog/2008/11/30/updating-nvidia-graphics-drivers-with-ubuntu-kernel-updates/)

Make sure you got all "installed" which [mikewhatever]("http://ubuntuforums.org/member.php?u=160645") wrote (I checked with Synaptic, Quick Search).

EDIT2:

This could be handy also: [http://ubuntuforums.org/showthread.php?t=373003&page=3](http://ubuntuforums.org/showthread.php?t=373003&page=3)

I got also GeForce 6200 AGP.

EDIT3:

Checked my xorgconfig too see how it looks now, interesting parts are:
Backup configuration first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```You can name 'xorg.conf.backup' xorg.conf part how you like, so you could later find it again and replace messed up configuration file with working one.
```
sudo gedit /etc/X11/xorg.conf
``````
Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```I remember from manual install times in modules were 'type1' and 'freetype' which could not be loaded on Ubuntu startup which lead to NVIDIA kernel module failure. GLX in modules is a hint, checked which glx things I got installed:
mesa-utils (This package provides several basic GL utilities built by Mesa, including
glxinfo and glxgears.)
libglitz-glx1 (The GLX backend for the Glitz OpenGL 2D graphics library.)
rss-glx (Really Slick Screensavers GLX Port) <- Seems not important
libgl1-mesa-glx (A free implementation of the OpenGL API -- GLX runtime) <- looks important, module glx?
xscreensaver-gl (GL(Mesa) screen hacks for xscreensaver) <- not important, screen savers for Open GL
xscreensaver-data (data files to be shared among screensaver frontends) <- containing more than 200 screen savers. Goes togheter with upper package.

Everything were latest versions.

EDIT4:
Got interested in this manual install and kernel problems, in sole Ubuntu is on top of Linux kernel, GLX is open source version of OpenGL for Windows? GL stands for OpenGL and X is for xserver. As I have understood, good link to read: [http://www.ntlug.org/archive/tp/glx_ccox/glx.html](http://www.ntlug.org/archive/tp/glx_ccox/glx.html)

There is link to setting up glx, same libglx.soxserver-xorg-core has caused me problems (not there, broken links, Ubuntu is using odd links which lead to new folder, maybe familiar from mounting *.iso images.)

EDIT5:
Mesa3D is OpenGL version for Linux, mesa packages which I have:
libgl1-mesa-glx
libgl1-mesa-dri
mesa-utils
libglu1-mesa
xscreensaver-gl (screensaver for xserver things, not important)

---

### Post by nsfzone on 2009-08-12
thanx to sooda, it works fine with mine... compiz works smooth after restart...:P

---

