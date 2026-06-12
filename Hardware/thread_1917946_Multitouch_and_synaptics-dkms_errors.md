---
title: "Multitouch and synaptics-dkms errors"
date: 2012-01-31
forum: Hardware
---

### Post by Dan Pat on 2012-01-31
I originally posted this in Absolute Beginners, but I think that was the wrong forum for this topic. I can't really gauge as a Linux beginner. Anyway, here's my original post:

I'm running Ubuntu 11.10 on an HP Envy 14 installed with the Desktop CD.  I'm also dual booting with Windows 7. This is only my second week using  Linux and no other threads I've found online have solved my problem, so  hopefully I can get some useful support here. 

When I first installed Ubuntu, my system supported two finger scrolling,  two fingers for right click, and three fingers for middle mouse button,  but I have since lost that functionality. Currently, I can right click with two fingers if I'm very careful,  but it requires multiple attempts to keep the dialogue open so  that I can select an option. Three finger clicking for middle mouse button actions is even worse and entirely unusable. Two finger scrolling does not work at all.  If I place one finger on the pad after another, the cursor jumps across  the screen.

One potential fix that I found online on [a blog specific to running Ubuntu on the Envy 14 ]("http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html#comment-form")involves installing "synaptics-dkms_1.1.1_all.deb", but I receive errors when installing it:

```
dan@dan-HP-ENVY-14-Notebook-PC:~/Downloads$ sudo dpkg -i synaptics-dkms_1.1.1_all.deb
Selecting previously deselected package synaptics-dkms.
(Reading database ... 173635 files and directories currently installed.)
Unpacking synaptics-dkms (from synaptics-dkms_1.1.1_all.deb) ...
Setting up synaptics-dkms (1.1.1) ...
Loading new synaptics-1.1.1 DKMS files...

Loading tarball for synaptics-1.1.1

DKMS: ldtarball Completed.

Creating symlink /var/lib/dkms/synaptics/1.1.1/source ->
                 /usr/src/synaptics-1.1.1

DKMS: add Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.0.0-14-generic -C  /lib/modules/3.0.0-14-generic/build  SUBDIRS=/var/lib/dkms/synaptics/1.1.1/build modules....(bad exit status:  2)
ERROR (dkms apport): binary package for synaptics: 1.1.1 not found
Error! Bad return status for module build on kernel: 3.0.0-14-generic (x86_64)
Consult /var/lib/dkms/synaptics/1.1.1/build/make.log for more information.
dpkg: error processing synaptics-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 synaptics-dkms

```I'm not sure these problems are related, but I can only guess  that these errors are hindering my progress. I've tried uninstalling and  reinstalling dkms to no avail. I've exhausted all the relevant Google  searches I can think of and I've reached the end of my limited knowledge  of the topic. I would really just like to be able to use two finger  scrolling and three fingers for middle mouse button. 

Thanks in advance for your help! :grin:

(Since this original post, I have reinstalled Ubuntu and had the same results. Multitouch works as it should for 3 or 4 boots, but then suddenly reverts back to the unpredictable state described above for seemingly no reason. I love Ubuntu except for a few bugs like this one. Help me keep it as my main OS!)

---

