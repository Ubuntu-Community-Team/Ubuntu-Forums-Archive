---
title: "link group x86_64-linux-gnu_gl_conf is broken"
date: 2015-01-14
forum: Hardware
---

### Post by Handssolow on 2015-01-14
I am still making no progress in installing the latest AMD Omega graphics in 14.04, link group x86_64-linux-gnu_gl_conf is broken
Attempting to install install the package libgl1-mesa-glx, link group x86_64-linux-gnu_gl_conf is broken
no success from sudo update-alternatives --auto x86_64-linux-gnu_gl_conf, link group x86_64-linux-gnu_gl_conf is broken

Perhaps when I purged fglrx* in the past or I have deleted an important link in the past.

Can someone please shed some likely reason for this message and it's background.
Does a new link need to be created?

---

### Post by Handssolow on 2015-01-25
bump
Aren't there any experts in this Forum able to offer some explanation what&#8217;s going wrong or even better some constructive suggestions?
A simple search shows up many folk getting this message when the AMD propitiatory driver fails to load then drops back to mesa.

What and where is/are the broken link(s)?

---

### Post by steeldriver on 2015-01-25
What does 

```

update-alternatives --query x86_64-linux-gnu_gl_conf

```
actually say? IIRC in the past I have resorted to removing all links from a troublesome group and starting over - but let's take a look before we go all medieval

---

### Post by Handssolow on 2015-01-26
Thanks for your reply.
Here the terminal output but I have no knowledge in this area.

Handssolow-desktop:~$ update-alternatives --query x86_64-linux-gnu_gl_conf
Name: x86_64-linux-gnu_gl_conf
Link: /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf
Slaves:
 x86_64-linux-gnu_xorg_extra_modules /usr/lib/x86_64-linux-gnu/xorg/extra-modules
Status: auto
Best: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Value: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf

Alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Priority: 500
Slaves:
 x86_64-linux-gnu_xorg_extra_modules /usr/lib/x86_64-linux-gnu/xorg/x11-extra-modules

I did an Ubuntu software update and noticed some there were some mesa related packages so had another go at installing the Omega driver. 
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide)

For now I have to modify the fglrx-core package because of a conflict with libopencl1 as I want to use PlayOnLinux Wine. I understand it will be March before the Ubuntu repository will have this fixed.

Installing the Omega deb packages I see this-

depmod..... 

DKMS: install completed. 
update-initramfs: deferring update (trigger activated) 
Setting up fglrx-dev (2:14.501-0ubuntu1) ... 
Setting up fglrx (2:14.501-0ubuntu1) ... 
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken 
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode 
Processing triggers for ureadahead (0.100.0-16) ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... 
Setting up fglrx-amdcccle (2:14.501-0ubuntu1) ... 
Processing triggers for mime-support (3.54ubuntu1.1) ... 
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
Processing triggers for initramfs-tools (0.103ubuntu4.2) ... 
update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic 
Processing triggers for libc-bin (2.19-0ubuntu6.5) &#8230;

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string: 2.1 Mesa 10.1.3


Uninstalling fglrx packages in synaptic because graphics are unusable for game play 

 (synaptic:4212): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 346865 files and directories currently installed.)
Removing fglrx-amdcccle (2:14.501-0ubuntu1) ...
Removing fglrx-dev (2:14.501-0ubuntu1) ...
Removing fglrx (2:14.501-0ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link
Removing fglrx-core (2:14.501-0ubuntu1) ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gfxcore_conf to auto mode
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic

The best I get is to use the open source driver by following the advice in the link above-

sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati

---

