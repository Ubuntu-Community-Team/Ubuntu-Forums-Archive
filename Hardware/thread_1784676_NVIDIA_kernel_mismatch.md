---
title: "NVIDIA kernel mismatch"
date: 2011-06-17
forum: Hardware
---

### Post by danilius on 2011-06-17
Whenever I reboot, the nVidia driver has to be reinstalled to get to the  desktop. I have tried shutting down GDM, running nvidia-xconfig and  then restarting GDM, but that is a hit-and-miss affair, and usually only  a driver reinstall works.

Naturally, I don't want to do this every time either.

This is the message I found in nvidia-installer.log:
```

Kernel messages:
   [  185.099013] NVRM: make sure that this kernel module and all NVIDIA driver
   [  185.099014] NVRM: components have the same version.
   [  185.280038] NVRM: API mismatch: the client has the version 270.41.19, but
   [  185.280040] NVRM: this kernel module has the version 270.41.06.  Please
   [  185.280041] NVRM: make sure that this kernel module and all NVIDIA driver
   [  185.280042] NVRM: components have the same version.
   [  185.459426] NVRM: API mismatch: the client has the version 270.41.19, but
   [  185.459428] NVRM: this kernel module has the version 270.41.06.  Please
   [  185.459429] NVRM: make sure that this kernel module and all NVIDIA driver
   [  185.459430] NVRM: components have the same version.
   [  185.633259] NVRM: API mismatch: the client has the version 270.41.19, but
   [  185.633260] NVRM: this kernel module has the version 270.41.06.  Please
   [  185.633261] NVRM: make sure that this kernel module and all NVIDIA driver
   [  185.633262] NVRM: components have the same version.

```How can I change the kernel module? Is that in fact what needs to  be done? How come the driver works once installed and then stops  working after rebooting?

I have hunted around for a solution but nowhere.

Here's to hoping there is someone out there who has/can resolve/d this issue.

---

### Post by spleach on 2011-07-02
Just had this problem myself after upgrading to NVIDIA 275.09.07, apparently from 270.41.06 (then why do I only have v265 in my Downloads folder?)

I thought I'd removed all of the xserver-xorg-video-* drivers, but they all appear as installed, according to `aptitude search xserver | grep '^i'`. So I removed all of them except for -fbdev, -intel, -sisusb & -vesa drivers. I was then presented with the KDE login screen after reinstalling the NVIDIA drivers :)

Upon a reboot, I was taken back to a console login again :(

Surprisingly, I found `nvidia-current` installed. Ahhh, that's the ticket! Thought I'd already removed repository drivers and installed my own...

Anyway, when you first run the nvidia installer after uninstalling nvidia-current, you'll get a dozen or so warnings about the directory /usr/lib/nvidia-current. I just confirmed that this doesn't affect the install though, by making those directories and reinstalling, only to find empty directories there. So I removed them, reinstalled, and no fuss!

Hope that works for anyone else too.

---

### Post by danilius on 2011-07-04
I found this deb: nvidia-current_275.09.07-0ubuntu4_amd64.deb but in my frustration forgot to bookmark the source. It worked a charm.

---

### Post by madmaze on 2011-09-14
> **spleach said:**
> Just had this problem myself after upgrading to NVIDIA 275.09.07, apparently from 270.41.06 (then why do I only have v265 in my Downloads folder?)

I thought I'd removed all of the xserver-xorg-video-* drivers, but they all appear as installed, according to `aptitude search xserver | grep '^i'`. So I removed all of them except for -fbdev, -intel, -sisusb & -vesa drivers. I was then presented with the KDE login screen after reinstalling the NVIDIA drivers :)

Upon a reboot, I was taken back to a console login again :(

Surprisingly, I found `nvidia-current` installed. Ahhh, that's the ticket! Thought I'd already removed repository drivers and installed my own...

Anyway, when you first run the nvidia installer after uninstalling nvidia-current, you'll get a dozen or so warnings about the directory /usr/lib/nvidia-current. I just confirmed that this doesn't affect the install though, by making those directories and reinstalling, only to find empty directories there. So I removed them, reinstalled, and no fuss!

Hope that works for anyone else too.


Yes removing nvidia-current fixed my issue.. 
Just ignore all the errors you get while it tries to uninstall the old stuff

---

### Post by yngvewb on 2012-08-27
This fixed this issue for me: 

Remove nvidia drivers:

sudo apt-get purge nvidia*

Then go to system settings->Additional Drivers and activate NVIDIA current updates

---

