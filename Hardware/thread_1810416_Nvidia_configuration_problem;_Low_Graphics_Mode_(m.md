---
title: "Nvidia configuration problem; Low Graphics Mode (missing /lib file?)"
date: 2011-07-23
forum: Hardware
---

### Post by Wgimson on 2011-07-23
I've had problems with my Nvidia graphics card drivers after a fresh install of 10.04. My laptop went into "Low Graphics Mode". I followed the fix on this site...

    [http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04](http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04)

...and when  I ran ran....    
    ```
sudo modprobe nvidia
```.. I got a message "FATAL: module not found", or something to that effect.
I went back and printed out the output of....

    ```
sudo apt-get install nvidia-current
```...after purging all nvidia drivers and blacklisting the problematic ones.
Here it is, and I've bolded the important parts where something seems to
have gone wrong...

Selecting previously deselected package nvidia-current.
(Reading database ... 137109 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_195.36.24-[CODE]0ubuntu1~10.04_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
[U][B]update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)[/B][/U]
Loading new nvidia-current-195.36.24 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-33-generic-pae
Building for architecture i686
Building initial module for 2.6.32-33-generic-pae
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - _**No original module exists within this kernel**_
 - Installation
   - Installing to /lib/modules/2.6.32-33-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic-pae
Processing triggers for python-support ...

Any help fixing this would be much appreciated, as computing in this 'low graphics mode' is really lame (not to mention when I shut of the keyboard to use the mouse I can't do anything at all; no text nor GUIs will appear).

Thanks again, guys.

---

### Post by Wgimson on 2011-07-23
Well, I'm probably going to just reinstall and not download Nvidia's proprietary drivers.

---

