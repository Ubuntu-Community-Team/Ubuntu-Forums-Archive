---
title: "Problems with graphic card drivers GeForce GTX 550 Ti and Ubuntu 15.04"
date: 2015-07-01
forum: Hardware
---

### Post by kubanc on 2015-07-01
Hello,
My graphic card drivers worked well under Ubuntu 14.04, but my HDMI audio was not recognized. So I decided to upgrade my Ubuntu to version 14.10. After the upgrade I found out that my graphic card driver is not working well, so I decided to upgrade to the latest version of Ubuntu. That is 15.04.

At first every time I could not see the desktop only the log in window. But when I entered my password, the screen went black for a few moments and then the login screen came back.
So, I decided to install some other drivers. That managed to sort this problem out, so I was able to log in into the desktop.

But now, there is another problem. I cannot see the dash, or the panel on the top of my desktop. I can only see the desktop and the icons.

I have tried to install the drivers with this command:
```

sudo add-apt-repository -y ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-340 nvidia-settings

```

The solution did not work. This are the drivers that are installed at the moment
```
sudo dpkg -l | grep -i nvidia

ii bbswitch-dkms            0.7-2ubuntu1                               amd64 interface for toggling the power on nVidia Optimus video cards
rc libcuda1-304             304.125-0ubuntu2                         amd64 NVIDIA CUDA runtime library
ii libcuda1-304               340.76-0ubuntu2                          amd64 NVIDIA CUDA runtime library
ii nouveau-firmware        20091212-0ubuntu1                       all   Firmware for nVidia graphic cards
ii nvidia-340                  340.76-0ubuntu2                           amd64 NVIDIA binary driver - version 340.76
ii nvidia-opencl-icd-340   340.76-0ubuntu2                           amd64 NVIDIA OpenCL ICD
ii nvidia-prime                0.8.1                                           amd64 Tools to enable NVIDIA's Prime
ii nvidia-settings            352.21-0ubuntu0~xedgers 15.04.1    amd64 tool for configuring the NVIDIA graphic driver
```


I have tried to uninstall nvidia driver with the command:

```
sudo apt-get remove --purge nvidia-*
E: Unable to locate package nvidia-bug-report.log.gz
E: Couldn't find any package by regex 'nvidia-bug-report.log.gz'
E: Unable to locate package nvidia-bug-report.log.old.gz
E: Couldn't find any package by regex 'nvidia-bug-report.log.old.gz'
```

And I used this command to uninstall nvidia drivers:
```
sudo apt-get purge $(dpkg -l | awk '$2~/nvidia/ {print $2}')
```
But this did not delete the nouveau-firmware drivers.

I found out this solution, perhaps it will work: [https://www.benburwell.com/posts/getting-login-to-work-ubuntu-15.04-nvidia/](https://www.benburwell.com/posts/getting-login-to-work-ubuntu-15.04-nvidia/), but this solution is for the NVIDIA GeForce GTX 750
```
wget http://us.download.nvidia.com/XFree86/\   Linux-x86_64/349.16/NVIDIA-Linux-x86_64-349.16.run $ chmod u+x NVIDIA-Linux-x86_64-349.16.run $ sudo service lightdm stop $ sudo ./NVIDIA-Linux-x86_64-349.16.run 
```

I assume that I must uninstall all the previus driver for graphic card and install the right one?
With kindly regards,

---

### Post by dino99 on 2015-07-01
your first choice was the good one: nvidia-340 (or up); so now run > sudo apt-get purge nvidia* then > sudo apt-get install nvidia-340
the dash & icons issues might be related to 'unity'; check the options/settings with the unity-tweak-tool; or use gnome-shell

and as that system has made several dist-upgrades, think to clean the system with clean/autoclean/autoremove/gtkorphan it might help

---

### Post by Yellow Pasque on 2015-07-01
I would get rid of the xorg-edgers PPA and everything it installed (use ppa-purge). You don't need xorg-edgers for Ubuntu 15.04, because the latest stable driver for your card (340.76) is available in the standard repos.

> I found out this solution, perhaps it will work
NO. Not only does that specific driver version not support your card, but installing directly from the .run file (i.e. not a package) is a very bad idea.

---

### Post by kubanc on 2015-07-01
I have now deleted all the drivers with the command
```
sudo apt-get purge 'nvidia-*'
```

The command:
```
sudo apt-get purge nvidia-*
``` does not work.

I have removed the ppa with the command:
```
sudo add-apt-repository --remove ppa:xorg-edgers/ppa
```

and have installed the drivers with the command:
```
sudo apt-get install nvidia-340
```

After that I have restarted the computer and the result is the same.
I still cannot see dock or menu at the top. If I click on the desktop with the right mouse button I get a menu, but this menu has a big black border. I am assuming that 3D support for unity is not working.

This are the drivers that are installed at the momen:
```
sudo dpkg -l | grep -i nvidia
ii bbswitch-dkms            0.7-2ubuntu1                               amd64 interface for toggling the power on nVidia Optimus video cards
ii libcuda1-340            340.76-0ubuntu2                            amd64 NVIDIA CUDA runtime library
ii nvidia-340                  340.76-0ubuntu2                           amd64 NVIDIA binary driver - version 340.76
ii nvidia-opencl-icd-340   340.76-0ubuntu2                           amd64 NVIDIA OpenCL ICD
ii nvidia-prime                0.8.1                                           amd64 Tools to enable NVIDIA's Prime
ii nvidia-settings	   346.59-0Ubuntu1			amd65 Tool for configuring the NVIDIA graphics driver

```

I have also done the
```
sudo apt-get autoremove
```

---

### Post by Yellow Pasque on 2015-07-01
```
sudo apt-get install ppa-purge
sudo ppa-purge xorg-edgers
sudo apt-get update
sudo apt-get install nvidia-340
```

BTW, you don't need to worry about nouveau-firmware package. It won't interfere with nvidia proprietary driver.

---

### Post by kubanc on 2015-07-01
When I do
```
sudo ppa-purge xorg-edgers
```
I get
```
Updating package lists
w: There is no public key available for the following IDs:
63F7D4AFF6D61D45
PPA to be removed: xorg-edgers-ppa
Warning: Could not find package list for PPA: xorg-edgers-ppa
```

---

### Post by kubanc on 2015-07-01
I've added this code:
```
[COLOR=#111111][FONT=Consolas]sudo add-apt-repository ppa:xorg-edgers/ppa [/FONT][/COLOR]
```
to solve the problem with not finding the package, but the problem is still the same.

---

### Post by dino99 on 2015-07-01
i see your hardware is provided with 'optimus'; so check that 'nvidia-prime' & 'bbswitch-dkms' packages are installed. Also check into the bios/uefi how optimus is set

---

### Post by kubanc on 2015-07-01
I have also installed this drivers:
```
ii bbswitch-dkms 0.7-2ubuntu1 amd64 Interface for toggling the power on Nvidia Optimus Video Card
ii nvidia-prime 0.8.1 amd64 Tools to enable NVIDIA's Prime 
```

---

### Post by Yellow Pasque on 2015-07-01
> **dino99 said:**
> i see your hardware is provided with 'optimus'; so check that 'nvidia-prime' & 'bbswitch-dkms' packages are installed. Also check into the bios/uefi how optimus is set

How did you come to the conclusion that this is an Optimus laptop (or even a laptop at all)? A GTX 550 Ti is a discrete graphics card used in desktops.

```
I've added this code: to solve the problem with not finding the package, but the problem is still the same.
```
You're getting way ahead of me. I gave you the ppa-purge command to make sure xorg-edgers was removed (which it already was). You then went and added it back. Let's try it again:
Run ALL these commands, in order and give the output.
```
sudo apt-get install ppa-purge
sudo ppa-purge xorg-edgers
sudo apt-get update
sudo apt-get install nvidia-340
```

> I have also installed this drivers: bbswitch-dkms nvidia-prime
They're not really drivers (more like utilities), and they're not needed for a GTX 550Ti.

---

### Post by kubanc on 2015-07-01
Here is the output of the commands:
sudo apt-get install ppa-purge
sudo ppa-purge xorg-edgers
sudo apt-get update
sudo apt-get install nvidia-340
```
Reading package lists...Building dependency tree...
Reading state information...
ppa-purge is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
Updating packages lists
PPA to be removed: xorg-edgers ppa
Note: Not removing ppa-purge package
Package revert list generated:
 libdrm-intel1:amd64/vivid libdrm-intel1:i386/vivid libdrm-nouveau2:amd64/vivid 
libdrm-nouveau2:i386/vivid libdrm-radeon1:amd64/vivid libdrm-radeon1:i386/vivid 
libdrm2:amd64/vivid libdrm2:i386/vivid libegl1-mesa:amd64/vivid 
libgbm1:amd64/vivid libgl1-mesa-dri:amd64/vivid libgl1-mesa-dri:i386/vivid 
libgl1-mesa-glx:amd64/vivid libgl1-mesa-glx:i386/vivid 
libglapi-mesa:amd64/vivid libglapi-mesa:i386/vivid libgles1-mesa:amd64/vivid 
libgles2-mesa:amd64/vivid libosmesa6:amd64/vivid libosmesa6:i386/vivid 
libvdpau1:amd64/vivid libwayland-egl1-mesa:amd64/vivid 
libxatracker2:amd64/vivid xserver-xorg-video-ati/vivid 
xserver-xorg-video-intel/vivid xserver-xorg-video-radeon/vivid


Disabling xorg-edgers PPA from 
/etc/apt/sources.list.d/xorg-edgers-ubuntu-ppa-vivid.list
Updating packages lists
Reading package lists...
Building dependency tree...
Reading state information...
libdrm-intel1 is already the newest version.
libdrm-nouveau2 is already the newest version.
libdrm-radeon1 is already the newest version.
libdrm2 is already the newest version.
libegl1-mesa is already the newest version.
libgbm1 is already the newest version.
libgl1-mesa-dri is already the newest version.
libgl1-mesa-glx is already the newest version.
libglapi-mesa is already the newest version.
libgles1-mesa is already the newest version.
libgles2-mesa is already the newest version.
libosmesa6 is already the newest version.
libvdpau1 is already the newest version.
libwayland-egl1-mesa is already the newest version.
libxatracker2 is already the newest version.
xserver-xorg-video-ati is already the newest version.
xserver-xorg-video-radeon is already the newest version.
libdrm-intel1:i386 is already the newest version.
libdrm-nouveau2:i386 is already the newest version.
libdrm-radeon1:i386 is already the newest version.
libdrm2:i386 is already the newest version.
libgl1-mesa-dri:i386 is already the newest version.
libgl1-mesa-glx:i386 is already the newest version.
libglapi-mesa:i386 is already the newest version.
libosmesa6:i386 is already the newest version.
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
PPA purged successfully
Hit http://deb.opera.com stable InRelease
Ign http://archive.ubuntu.com vivid InRelease
Ign http://archive.ubuntu.com vivid-updates InRelease
Hit http://deb.opera.com stable/non-free amd64 Packages
Ign http://archive.ubuntu.com vivid-backports InRelease
Hit http://deb.opera.com stable/non-free i386 Packages
Ign http://archive.ubuntu.com vivid-security InRelease
Hit http://archive.ubuntu.com vivid Release.gpg
Hit http://archive.ubuntu.com vivid-updates Release.gpg
Hit http://archive.ubuntu.com vivid-backports Release.gpg
Hit http://archive.ubuntu.com vivid-security Release.gpg
Hit http://archive.ubuntu.com vivid Release
Hit http://archive.ubuntu.com vivid-updates Release
Hit http://archive.ubuntu.com vivid-backports Release
Ign http://deb.opera.com stable/non-free Translation-en_US
Hit http://archive.ubuntu.com vivid-security Release
Ign http://deb.opera.com stable/non-free Translation-en
Hit http://archive.ubuntu.com vivid/main Sources
Hit http://archive.ubuntu.com vivid/restricted Sources
Hit http://archive.ubuntu.com vivid/universe Sources
Hit http://archive.ubuntu.com vivid/multiverse Sources
Hit http://archive.ubuntu.com vivid/main amd64 Packages
Hit http://archive.ubuntu.com vivid/restricted amd64 Packages
Hit http://archive.ubuntu.com vivid/universe amd64 Packages
Hit http://archive.ubuntu.com vivid/multiverse amd64 Packages
Hit http://archive.ubuntu.com vivid/main i386 Packages
Hit http://archive.ubuntu.com vivid/restricted i386 Packages
Hit http://archive.ubuntu.com vivid/universe i386 Packages
Hit http://archive.ubuntu.com vivid/multiverse i386 Packages
Hit http://archive.ubuntu.com vivid/main Translation-en
Hit http://archive.ubuntu.com vivid/multiverse Translation-en
Hit http://archive.ubuntu.com vivid/restricted Translation-en
Hit http://archive.ubuntu.com vivid/universe Translation-en
Hit http://archive.ubuntu.com vivid-updates/main Sources
Hit http://archive.ubuntu.com vivid-updates/restricted Sources
Hit http://archive.ubuntu.com vivid-updates/universe Sources
Hit http://archive.ubuntu.com vivid-updates/multiverse Sources
Hit http://archive.ubuntu.com vivid-updates/main amd64 Packages
Hit http://archive.ubuntu.com vivid-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com vivid-updates/universe amd64 Packages
Hit http://archive.ubuntu.com vivid-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com vivid-updates/main i386 Packages
Hit http://archive.ubuntu.com vivid-updates/restricted i386 Packages
Hit http://archive.ubuntu.com vivid-updates/universe i386 Packages
Hit http://archive.ubuntu.com vivid-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com vivid-updates/main Translation-en
Hit http://archive.ubuntu.com vivid-updates/multiverse Translation-en
Hit http://archive.ubuntu.com vivid-updates/restricted Translation-en
Hit http://archive.ubuntu.com vivid-updates/universe Translation-en
Hit http://archive.ubuntu.com vivid-backports/main Sources
Hit http://archive.ubuntu.com vivid-backports/restricted Sources
Hit http://archive.ubuntu.com vivid-backports/universe Sources
Hit http://archive.ubuntu.com vivid-backports/multiverse Sources
Hit http://archive.ubuntu.com vivid-backports/main amd64 Packages
Hit http://archive.ubuntu.com vivid-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com vivid-backports/universe amd64 Packages
Hit http://archive.ubuntu.com vivid-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com vivid-backports/main i386 Packages
Hit http://archive.ubuntu.com vivid-backports/restricted i386 Packages
Hit http://archive.ubuntu.com vivid-backports/universe i386 Packages
Hit http://archive.ubuntu.com vivid-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com vivid-backports/main Translation-en
Hit http://archive.ubuntu.com vivid-backports/multiverse Translation-en
Hit http://archive.ubuntu.com vivid-backports/restricted Translation-en
Hit http://archive.ubuntu.com vivid-backports/universe Translation-en
Hit http://archive.ubuntu.com vivid-security/main Sources
Hit http://archive.ubuntu.com vivid-security/restricted Sources
Hit http://archive.ubuntu.com vivid-security/universe Sources
Hit http://archive.ubuntu.com vivid-security/multiverse Sources
Hit http://archive.ubuntu.com vivid-security/main amd64 Packages
Hit http://archive.ubuntu.com vivid-security/restricted amd64 Packages
Hit http://archive.ubuntu.com vivid-security/universe amd64 Packages
Hit http://archive.ubuntu.com vivid-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com vivid-security/main i386 Packages
Hit http://archive.ubuntu.com vivid-security/restricted i386 Packages
Hit http://archive.ubuntu.com vivid-security/universe i386 Packages
Hit http://archive.ubuntu.com vivid-security/multiverse i386 Packages
Hit http://archive.ubuntu.com vivid-security/main Translation-en
Hit http://archive.ubuntu.com vivid-security/multiverse Translation-en
Hit http://archive.ubuntu.com vivid-security/restricted Translation-en
Hit http://archive.ubuntu.com vivid-security/universe Translation-en
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  bbswitch-dkms lib32gcc1 libcuda1-340 libjansson4 libxnvctrl0
  nvidia-opencl-icd-340 nvidia-prime nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee
The following NEW packages will be installed:
  bbswitch-dkms lib32gcc1 libcuda1-340 libjansson4 libxnvctrl0 nvidia-340
  nvidia-opencl-icd-340 nvidia-prime nvidia-settings screen-resolution-extra
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/70.1 MB of archives.
After this operation, 330 MB of additional disk space will be used.
Do you want to continue? [Y/n] Selecting previously unselected package libjansson4:amd64.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 402391 files and directories currently installed.)
Preparing to unpack .../libjansson4_2.7-1ubuntu1_amd64.deb ...
Unpacking libjansson4:amd64 (2.7-1ubuntu1) ...
Selecting previously unselected package libcuda1-340.
Preparing to unpack .../libcuda1-340_340.76-0ubuntu2_amd64.deb ...
Unpacking libcuda1-340 (340.76-0ubuntu2) ...
Selecting previously unselected package libxnvctrl0.
Preparing to unpack .../libxnvctrl0_346.59-0ubuntu1_amd64.deb ...
Unpacking libxnvctrl0 (346.59-0ubuntu1) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a5.1~rc1-0ubuntu1_amd64.deb ...
Unpacking lib32gcc1 (1:5.1~rc1-0ubuntu1) ...
Selecting previously unselected package nvidia-340.
Preparing to unpack .../nvidia-340_340.76-0ubuntu2_amd64.deb ...
Unpacking nvidia-340 (340.76-0ubuntu2) ...
Selecting previously unselected package nvidia-opencl-icd-340.
Preparing to unpack .../nvidia-opencl-icd-340_340.76-0ubuntu2_amd64.deb ...
Unpacking nvidia-opencl-icd-340 (340.76-0ubuntu2) ...
Selecting previously unselected package bbswitch-dkms.
Preparing to unpack .../bbswitch-dkms_0.7-2ubuntu1_amd64.deb ...
Unpacking bbswitch-dkms (0.7-2ubuntu1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.1_amd64.deb ...
Unpacking nvidia-prime (0.8.1) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_346.59-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (346.59-0ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Setting up libjansson4:amd64 (2.7-1ubuntu1) ...
Setting up libcuda1-340 (340.76-0ubuntu2) ...
Setting up libxnvctrl0 (346.59-0ubuntu1) ...
Setting up lib32gcc1 (1:5.1~rc1-0ubuntu1) ...
Setting up nvidia-340 (340.76-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-340/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-340/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-340/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 137) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-340-340.76 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-21-generic
Building for architecture x86_64
Building initial module for 3.19.0-21-generic
Done.


nvidia_340:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-21-generic/updates/dkms/


nvidia_340_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-21-generic/updates/dkms/


depmod....


DKMS: install completed.
Setting up nvidia-opencl-icd-340 (340.76-0ubuntu2) ...
Setting up bbswitch-dkms (0.7-2ubuntu1) ...
Loading new bbswitch-0.7 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-21-generic
Building initial module for 3.19.0-21-generic
Done.


bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-21-generic/updates/dkms/


depmod....


DKMS: install completed.
Setting up nvidia-prime (0.8.1) ...
Setting up screen-resolution-extra (0.17.1) ...
Setting up nvidia-settings (346.59-0ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-21-generic
Processing triggers for ureadahead (0.100.0-19) ...



```

---

### Post by kubanc on 2015-07-01
This are the additiona drivers that I can see
[IMG]http://s28.postimg.org/chegb5nm5/IMG_20150701_174946.jpg[/IMG]

---

### Post by Yellow Pasque on 2015-07-01
Okay, so the driver successfully installed, but Unity is not working correctly. If I understand correctly, we're now at this point:
> I still cannot see dock or menu at the top. If I click on the desktop with the right mouse button I get a menu, but this menu has a big black border. I am assuming that 3D support for unity is not working.
If you can drop to the terminal (Ctrl+Alt+F1 if you can't get to it in Unity) and run this, it may fix the Unity problem:
```
sudo apt-get install nvidia-346
```
Reboot (or log out). If Unity still is distorted, copy/paste the contents of /var/log/Xorg.0.log file her (use code tags because it's a lot of text). You can also check glxinfo to make sure 3D is working properly and it's just a Unity issue:
```
glxinfo | grep OpenGL
```

Note: My apologies for having you install the 340 driver. I forgot that GTX 500 series (aka Fermi) is still supported in drivers newer than 340.xx branch. Despite that, 340.76 should still have worked, though.

---

### Post by kubanc on 2015-07-02
I've done this in terminal
sudo apt-get install nvidia-346
but id doesn't help..

Here is my glxinfo:
```
OpenGL vendor string: NVIDIA CorporationOpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL core profile version string: 4.4.0 NVIDIA 346.59
OpenGL core profile shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 346.59
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 NVIDIA 346.59
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:
```

any my Xorg.0.log
```
[     2.826] X.Org X Server 1.17.1
Release Date: 2015-02-10
[     2.826] X Protocol Version 11, Revision 0
[     2.826] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[     2.826] Current Operating System: Linux kubanc-desktop 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:31:11 UTC 2015 x86_64
[     2.826] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-21-generic root=UUID=5a471571-a23d-437d-836b-73ae7d68cef1 ro nomodeset nomodeset
[     2.826] Build Date: 19 March 2015  09:26:59AM
[     2.826] xorg-server 2:1.17.1-0ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[     2.826] Current version of pixman: 0.32.6
[     2.826]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     2.826] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     2.826] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul  2 16:35:04 2015
[     2.827] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     2.829] (==) No Layout section.  Using the first Screen section.
[     2.829] (==) No screen section available. Using defaults.
[     2.829] (**) |-->Screen "Default Screen Section" (0)
[     2.829] (**) |   |-->Monitor "<default monitor>"
[     2.829] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     2.829] (==) Automatically adding devices
[     2.829] (==) Automatically enabling devices
[     2.829] (==) Automatically adding GPU devices
[     2.830] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     2.830]     Entry deleted from font path.
[     2.830] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     2.830]     Entry deleted from font path.
[     2.830] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     2.830]     Entry deleted from font path.
[     2.830] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     2.830]     Entry deleted from font path.
[     2.831] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     2.831]     Entry deleted from font path.
[     2.831] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     2.831] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     2.831] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     2.831] (II) Loader magic: 0x7ff63b3e8d80
[     2.831] (II) Module ABI versions:
[     2.831]     X.Org ANSI C Emulation: 0.4
[     2.831]     X.Org Video Driver: 19.0
[     2.831]     X.Org XInput driver : 21.0
[     2.831]     X.Org Server Extension : 9.0
[     2.831] (II) xfree86: Adding drm device (/dev/dri/card0)
[     2.832] (--) PCI: (0:0:2:0) 8086:0162:1849:0162 rev 9, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[     2.832] (--) PCI:*(0:1:0:0) 10de:1244:1043:83be rev 161, Mem @ 0xf4000000/33554432, 0xe0000000/134217728, 0xe8000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     2.832] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     2.832] (II) "glx" will be loaded by default.
[     2.832] (WW) "xmir" is not to be loaded by default. Skipping.
[     2.832] (II) LoadModule: "glx"
[     2.832] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     2.904] (II) Module glx: vendor="NVIDIA Corporation"
[     2.904]     compiled for 4.0.2, module version = 1.0.0
[     2.904]     Module class: X.Org Server Extension
[     2.905] (II) NVIDIA GLX Module  346.59  Tue Mar 31 13:38:58 PDT 2015
[     2.905] (==) Matched nvidia as autoconfigured driver 0
[     2.905] (==) Matched nouveau as autoconfigured driver 1
[     2.905] (==) Matched nvidia as autoconfigured driver 2
[     2.905] (==) Matched nouveau as autoconfigured driver 3
[     2.905] (==) Matched modesetting as autoconfigured driver 4
[     2.905] (==) Matched fbdev as autoconfigured driver 5
[     2.905] (==) Matched vesa as autoconfigured driver 6
[     2.905] (==) Assigned the driver to the xf86ConfigLayout
[     2.905] (II) LoadModule: "nvidia"
[     2.905] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     2.911] (II) Module nvidia: vendor="NVIDIA Corporation"
[     2.911]     compiled for 4.0.2, module version = 1.0.0
[     2.911]     Module class: X.Org Video Driver
[     2.911] (II) LoadModule: "nouveau"
[     2.912] (WW) Warning, couldn't open module nouveau
[     2.912] (II) UnloadModule: "nouveau"
[     2.912] (II) Unloading nouveau
[     2.912] (EE) Failed to load module "nouveau" (module does not exist, 0)
[     2.912] (II) LoadModule: "modesetting"
[     2.912] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.913] (II) Module modesetting: vendor="X.Org Foundation"
[     2.913]     compiled for 1.17.1, module version = 1.17.1
[     2.913]     Module class: X.Org Video Driver
[     2.913]     ABI class: X.Org Video Driver, version 19.0
[     2.913] (II) LoadModule: "fbdev"
[     2.913] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.913] (II) Module fbdev: vendor="X.Org Foundation"
[     2.913]     compiled for 1.17.1, module version = 0.4.4
[     2.913]     Module class: X.Org Video Driver
[     2.913]     ABI class: X.Org Video Driver, version 19.0
[     2.913] (II) LoadModule: "vesa"
[     2.913] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.913] (II) Module vesa: vendor="X.Org Foundation"
[     2.913]     compiled for 1.17.1, module version = 2.3.3
[     2.913]     Module class: X.Org Video Driver
[     2.914]     ABI class: X.Org Video Driver, version 19.0
[     2.914] (==) Matched nvidia as autoconfigured driver 0
[     2.914] (==) Matched nouveau as autoconfigured driver 1
[     2.914] (==) Matched nvidia as autoconfigured driver 2
[     2.914] (==) Matched nouveau as autoconfigured driver 3
[     2.914] (==) Matched modesetting as autoconfigured driver 4
[     2.914] (==) Matched fbdev as autoconfigured driver 5
[     2.914] (==) Matched vesa as autoconfigured driver 6
[     2.914] (==) Assigned the driver to the xf86ConfigLayout
[     2.914] (II) LoadModule: "nvidia"
[     2.914] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     2.914] (II) Module nvidia: vendor="NVIDIA Corporation"
[     2.914]     compiled for 4.0.2, module version = 1.0.0
[     2.914]     Module class: X.Org Video Driver
[     2.914] (II) UnloadModule: "nvidia"
[     2.914] (II) Unloading nvidia
[     2.914] (II) Failed to load module "nvidia" (already loaded, 32758)
[     2.914] (II) LoadModule: "nouveau"
[     2.914] (WW) Warning, couldn't open module nouveau
[     2.914] (II) UnloadModule: "nouveau"
[     2.914] (II) Unloading nouveau
[     2.914] (EE) Failed to load module "nouveau" (module does not exist, 0)
[     2.914] (II) LoadModule: "modesetting"
[     2.914] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.914] (II) Module modesetting: vendor="X.Org Foundation"
[     2.914]     compiled for 1.17.1, module version = 1.17.1
[     2.914]     Module class: X.Org Video Driver
[     2.914]     ABI class: X.Org Video Driver, version 19.0
[     2.914] (II) UnloadModule: "modesetting"
[     2.914] (II) Unloading modesetting
[     2.914] (II) Failed to load module "modesetting" (already loaded, 0)
[     2.914] (II) LoadModule: "fbdev"
[     2.914] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.914] (II) Module fbdev: vendor="X.Org Foundation"
[     2.914]     compiled for 1.17.1, module version = 0.4.4
[     2.914]     Module class: X.Org Video Driver
[     2.914]     ABI class: X.Org Video Driver, version 19.0
[     2.914] (II) UnloadModule: "fbdev"
[     2.914] (II) Unloading fbdev
[     2.914] (II) Failed to load module "fbdev" (already loaded, 0)
[     2.914] (II) LoadModule: "vesa"
[     2.914] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.914] (II) Module vesa: vendor="X.Org Foundation"
[     2.914]     compiled for 1.17.1, module version = 2.3.3
[     2.914]     Module class: X.Org Video Driver
[     2.914]     ABI class: X.Org Video Driver, version 19.0
[     2.914] (II) UnloadModule: "vesa"
[     2.914] (II) Unloading vesa
[     2.914] (II) Failed to load module "vesa" (already loaded, 0)
[     2.914] (II) NVIDIA dlloader X Driver  346.59  Tue Mar 31 13:17:41 PDT 2015
[     2.914] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     2.914] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     2.914] (II) FBDEV: driver for framebuffer: fbdev
[     2.914] (II) VESA: driver for VESA chipsets: vesa
[     2.914] (++) using VT number 7


[     2.924] (II) Loading sub module "fb"
[     2.924] (II) LoadModule: "fb"
[     2.924] (II) Loading /usr/lib/xorg/modules/libfb.so
[     2.925] (II) Module fb: vendor="X.Org Foundation"
[     2.925]     compiled for 1.17.1, module version = 1.0.0
[     2.925]     ABI class: X.Org ANSI C Emulation, version 0.4
[     2.925] (II) Loading sub module "wfb"
[     2.925] (II) LoadModule: "wfb"
[     2.925] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     2.926] (II) Module wfb: vendor="X.Org Foundation"
[     2.926]     compiled for 1.17.1, module version = 1.0.0
[     2.926]     ABI class: X.Org ANSI C Emulation, version 0.4
[     2.926] (II) Loading sub module "ramdac"
[     2.926] (II) LoadModule: "ramdac"
[     2.926] (II) Module "ramdac" already built-in
[     2.926] (WW) Falling back to old probe method for modesetting
[     2.926] (WW) Falling back to old probe method for fbdev
[     2.926] (II) Loading sub module "fbdevhw"
[     2.926] (II) LoadModule: "fbdevhw"
[     2.927] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     2.927] (II) Module fbdevhw: vendor="X.Org Foundation"
[     2.927]     compiled for 1.17.1, module version = 0.0.2
[     2.927]     ABI class: X.Org Video Driver, version 19.0
[     2.927] (EE) open /dev/fb0: No such file or directory
[     2.927] (EE) open /dev/fb0: No such file or directory
[     2.927] (WW) Falling back to old probe method for vesa
[     2.927] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     2.927] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     2.927] (==) NVIDIA(0): RGB weight 888
[     2.927] (==) NVIDIA(0): Default visual is TrueColor
[     2.927] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     2.927] (**) NVIDIA(0): Enabling 2D acceleration
[     3.406] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[     3.406] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 550 Ti (GF116) at PCI:1:0:0 (GPU-0)
[     3.406] (--) NVIDIA(0): Memory: 1048576 kBytes
[     3.406] (--) NVIDIA(0): VideoBIOS: 70.26.20.00.00
[     3.406] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     3.426] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 550 Ti at PCI:1:0:0
[     3.426] (--) NVIDIA(0):     CRT-0
[     3.426] (--) NVIDIA(0):     DELL 2408WFP (CRT-1) (boot, connected)
[     3.426] (--) NVIDIA(0):     DFP-0
[     3.426] (--) NVIDIA(0):     DFP-1
[     3.426] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     3.426] (--) NVIDIA(GPU-0): DELL 2408WFP (CRT-1): 400.0 MHz maximum pixel clock
[     3.426] (--) NVIDIA(0): DFP-0: Internal TMDS
[     3.426] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     3.426] (--) NVIDIA(0): DFP-1: Internal TMDS
[     3.426] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     3.426] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     3.426] (**) NVIDIA(0):     device DELL 2408WFP (CRT-1) (Using EDID frequencies has
[     3.426] (**) NVIDIA(0):     been enabled on all display devices.)
[     3.426] (==) NVIDIA(0): 
[     3.426] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     3.426] (==) NVIDIA(0):     will be used as the requested mode.
[     3.426] (==) NVIDIA(0): 
[     3.426] (II) NVIDIA(0): Validated MetaModes:
[     3.426] (II) NVIDIA(0):     "CRT-1:nvidia-auto-select"
[     3.426] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[     3.452] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[     3.452] (--) NVIDIA(0):     option
[     3.452] (II) UnloadModule: "modesetting"
[     3.452] (II) Unloading modesetting
[     3.452] (II) UnloadModule: "fbdev"
[     3.452] (II) Unloading fbdev
[     3.452] (II) UnloadSubModule: "fbdevhw"
[     3.452] (II) Unloading fbdevhw
[     3.452] (II) UnloadModule: "vesa"
[     3.452] (II) Unloading vesa
[     3.452] (--) Depth 24 pixmap format is 32 bpp
[     3.452] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     3.452] (II) NVIDIA:     access.
[     3.474] (II) NVIDIA(0): Setting mode "CRT-1:nvidia-auto-select"
[     3.564] (==) NVIDIA(0): Disabling shared memory pixmaps
[     3.564] (==) NVIDIA(0): Backing store enabled
[     3.564] (==) NVIDIA(0): Silken mouse enabled
[     3.564] (==) NVIDIA(0): DPMS enabled
[     3.564] (II) Loading sub module "dri2"
[     3.564] (II) LoadModule: "dri2"
[     3.564] (II) Module "dri2" already built-in
[     3.564] (II) NVIDIA(0): [DRI2] Setup complete
[     3.564] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     3.565] (--) RandR disabled
[     3.567] (II) SELinux: Disabled on system
[     3.568] (II) Initializing extension GLX
[     3.568] (II) Indirect GLX disabled.(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.589] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.589] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.589] (II) LoadModule: "evdev"
[     3.589] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.590] (II) Module evdev: vendor="X.Org Foundation"
[     3.590]     compiled for 1.16.0, module version = 2.9.0
[     3.590]     Module class: X.Org XInput Driver
[     3.590]     ABI class: X.Org XInput driver, version 21.0
[     3.590] (II) Using input driver 'evdev' for 'Power Button'
[     3.590] (**) Power Button: always reports core events
[     3.590] (**) evdev: Power Button: Device: "/dev/input/event1"
[     3.590] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.590] (--) evdev: Power Button: Found keys
[     3.590] (II) evdev: Power Button: Configuring as keyboard
[     3.590] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     3.590] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.590] (**) Option "xkb_rules" "evdev"
[     3.590] (**) Option "xkb_model" "pc105"
[     3.590] (**) Option "xkb_layout" "si"
[     3.591] (II) XKB: reuse xkmfile /var/lib/xkb/server-382E998F79C55FE563EE3D1572FEC9D6349EB92C.xkm
[     3.592] (II) config/udev: Adding input device Video Bus (/dev/input/event2)
[     3.592] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     3.592] (II) Using input driver 'evdev' for 'Video Bus'
[     3.592] (**) Video Bus: always reports core events
[     3.592] (**) evdev: Video Bus: Device: "/dev/input/event2"
[     3.592] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     3.592] (--) evdev: Video Bus: Found keys
[     3.592] (II) evdev: Video Bus: Configuring as keyboard
[     3.592] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event2"
[     3.592] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     3.592] (**) Option "xkb_rules" "evdev"
[     3.592] (**) Option "xkb_model" "pc105"
[     3.592] (**) Option "xkb_layout" "si"
[     3.592] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.592] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.592] (II) Using input driver 'evdev' for 'Power Button'
[     3.592] (**) Power Button: always reports core events
[     3.592] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.592] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.592] (--) evdev: Power Button: Found keys
[     3.592] (II) evdev: Power Button: Configuring as keyboard
[     3.592] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     3.592] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     3.592] (**) Option "xkb_rules" "evdev"
[     3.592] (**) Option "xkb_model" "pc105"
[     3.592] (**) Option "xkb_layout" "si"
[     3.592] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[     3.592] (II) No input driver specified, ignoring this device.
[     3.592] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event15)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event16)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event17)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event7)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event8)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event10)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event11)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.593] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event3)
[     3.593] (II) No input driver specified, ignoring this device.
[     3.593] (II) This device may have been added with another device file.
[     3.594] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event4)
[     3.594] (II) No input driver specified, ignoring this device.
[     3.594] (II) This device may have been added with another device file.
[     3.594] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event5)
[     3.594] (II) No input driver specified, ignoring this device.
[     3.594] (II) This device may have been added with another device file.
[     3.594] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event6)
[     3.594] (II) No input driver specified, ignoring this device.
[     3.594] (II) This device may have been added with another device file.
[     3.594] (II) config/udev: Adding input device Logitech Performance MX (/dev/input/event12)
[     3.594] (**) Logitech Performance MX: Applying InputClass "evdev pointer catchall"
[     3.594] (II) Using input driver 'evdev' for 'Logitech Performance MX'
[     3.594] (**) Logitech Performance MX: always reports core events
[     3.594] (**) evdev: Logitech Performance MX: Device: "/dev/input/event12"
[     3.594] (--) evdev: Logitech Performance MX: Vendor 0x46d Product 0x101a
[     3.594] (--) evdev: Logitech Performance MX: Found 20 mouse buttons
[     3.594] (--) evdev: Logitech Performance MX: Found scroll wheel(s)
[     3.594] (--) evdev: Logitech Performance MX: Found relative axes
[     3.594] (--) evdev: Logitech Performance MX: Found x and y relative axes
[     3.594] (II) evdev: Logitech Performance MX: Configuring as mouse
[     3.594] (II) evdev: Logitech Performance MX: Adding scrollwheel support
[     3.594] (**) evdev: Logitech Performance MX: YAxisMapping: buttons 4 and 5
[     3.594] (**) evdev: Logitech Performance MX: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.594] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.7/4-1.7:1.2/0003:046D:C52B.0003/0003:046D:101A.0007/input/input15/event12"
[     3.594] (II) XINPUT: Adding extended input device "Logitech Performance MX" (type: MOUSE, id 9)
[     3.594] (II) evdev: Logitech Performance MX: initialized for relative axes.
[     3.594] (**) Logitech Performance MX: (accel) keeping acceleration scheme 1
[     3.594] (**) Logitech Performance MX: (accel) acceleration profile 0
[     3.594] (**) Logitech Performance MX: (accel) acceleration factor: 2.000
[     3.594] (**) Logitech Performance MX: (accel) acceleration threshold: 4
[     3.594] (II) config/udev: Adding input device Logitech Performance MX (/dev/input/mouse0)
[     3.594] (II) No input driver specified, ignoring this device.
[     3.594] (II) This device may have been added with another device file.
[     3.595] (II) config/udev: Adding input device Logitech K800 (/dev/input/event13)
[     3.595] (**) Logitech K800: Applying InputClass "evdev keyboard catchall"
[     3.595] (II) Using input driver 'evdev' for 'Logitech K800'
[     3.595] (**) Logitech K800: always reports core events
[     3.595] (**) evdev: Logitech K800: Device: "/dev/input/event13"
[     3.595] (--) evdev: Logitech K800: Vendor 0x46d Product 0x2010
[     3.595] (--) evdev: Logitech K800: Found 1 mouse buttons
[     3.595] (--) evdev: Logitech K800: Found scroll wheel(s)
[     3.595] (--) evdev: Logitech K800: Found relative axes
[     3.595] (II) evdev: Logitech K800: Forcing relative x/y axes to exist.
[     3.595] (--) evdev: Logitech K800: Found absolute axes
[     3.595] (II) evdev: Logitech K800: Forcing absolute x/y axes to exist.
[     3.595] (--) evdev: Logitech K800: Found keys
[     3.595] (II) evdev: Logitech K800: Configuring as mouse
[     3.595] (II) evdev: Logitech K800: Configuring as keyboard
[     3.595] (II) evdev: Logitech K800: Adding scrollwheel support
[     3.595] (**) evdev: Logitech K800: YAxisMapping: buttons 4 and 5
[     3.595] (**) evdev: Logitech K800: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.595] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.8/4-1.8:1.2/0003:046D:C52B.0006/0003:046D:2010.0008/input/input16/event13"
[     3.595] (II) XINPUT: Adding extended input device "Logitech K800" (type: KEYBOARD, id 10)
[     3.595] (**) Option "xkb_rules" "evdev"
[     3.595] (**) Option "xkb_model" "pc105"
[     3.595] (**) Option "xkb_layout" "si"
[     3.595] (II) evdev: Logitech K800: initialized for relative axes.
[     3.595] (WW) evdev: Logitech K800: ignoring absolute axes.
[     3.595] (**) Logitech K800: (accel) keeping acceleration scheme 1
[     3.595] (**) Logitech K800: (accel) acceleration profile 0
[     3.595] (**) Logitech K800: (accel) acceleration factor: 2.000
[     3.595] (**) Logitech K800: (accel) acceleration threshold: 4
[     4.337] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.337] (**) NVIDIA(0):     device DELL 2408WFP (CRT-1) (Using EDID frequencies has
[     4.337] (**) NVIDIA(0):     been enabled on all display devices.)
[     4.370] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.370] (**) NVIDIA(0):     device DELL 2408WFP (CRT-1) (Using EDID frequencies has
[     4.370] (**) NVIDIA(0):     been enabled on all display devices.)
[     4.378] (II) XKB: reuse xkmfile /var/lib/xkb/server-382E998F79C55FE563EE3D1572FEC9D6349EB92C.xkm
[     4.784] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.784] (**) NVIDIA(0):     device DELL 2408WFP (CRT-1) (Using EDID frequencies has
[     4.784] (**) NVIDIA(0):     been enabled on all display devices.)
[     4.817] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.817] (**) NVIDIA(0):     device DELL 2408WFP (CRT-1) (Using EDID frequencies has
[     4.817] (**) NVIDIA(0):     been enabled on all display devices.)
[     8.363] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     8.363] (**) NVIDIA(0):     device DELL 2408WFP (CRT-1) (Using EDID frequencies has
[     8.363] (**) NVIDIA(0):     been enabled on all display devices.)
[     8.491] (II) XKB: reuse xkmfile /var/lib/xkb/server-E8B795759068327308981EE742CE9783A8337341.xkm
[     8.500] (II) XKB: reuse xkmfile /var/lib/xkb/server-E8B795759068327308981EE742CE9783A8337341.xkm
```

---

### Post by Yellow Pasque on 2015-07-02
It all looks good from a driver standpoint. 

The only other suggestions I have:
1. Try and reset Unity's graphics configuration: [http://ubuntuhandbook.org/index.php/2014/04/reset-unity-and-compiz-settings-in-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/reset-unity-and-compiz-settings-in-ubuntu-14-04/)
2. If 1 doesn't work, try absolute latest stable nvidia driver (nvidia-352) from this excellent PPA: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by kubanc on 2015-07-03
The commands:
```
[COLOR=#333333][FONT=Monaco]dconf reset -f /org/compiz/[/FONT][/COLOR]
```
and
```
[COLOR=#333333][FONT=Monaco]setsid unity[/FONT][/COLOR]
```

**SOLVED THE PROBLEM...**

Do I need and uninstall  the other drivers.
Should I install now nvidia drivers from their webpage?
But my HDMI audio is still not working. I am assuming I must create a new post for that

By the way, thank you Temüjin for you help ):P

---

### Post by Yellow Pasque on 2015-07-03
No. If everything's working well, you don't need a newer driver and you should just leave well enough alone.
> Should I install now nvidia drivers from their webpage?
NO. NEVER.

---

### Post by dino99 on 2015-07-03
> **kubanc said:**
> The commands:
```
[COLOR=#333333][FONT=Monaco]dconf reset -f /org/compiz/[/FONT][/COLOR]
```
and
```
[COLOR=#333333][FONT=Monaco]setsid unity[/FONT][/COLOR]
```

**SOLVED THE PROBLEM...**

But my HDMI audio is still not working.

This is becoming partially fixed (fully fixed with the most common chipsets, but not these rare ones yet) with the latest kernel (4.1 which will come with Wily soon) and the latest nvidia-352 and drm. If that hdmi problem is important for you, then think to upgrade to Wily

---

### Post by kubanc on 2015-07-03
I kinda need my HDMI because through HDMI I am connected to SONY STR-DH520
But I would not like to upgrade to Wily because it is still in the development phase.

---

### Post by dino99 on 2015-07-03
> **kubanc said:**
> I kinda need my HDMI because through HDMI I am connected to SONY STR-DH520
But I would not like to upgrade to Wily because it is still in the development phase.

only my own taste, to say wily is less buggy that all the other releases; if your are scared, then simply deactivate the 'proposed' archive and only use packages in 'main'

---

### Post by grahammechanical on 2015-07-03
> I kinda need my HDMI because through HDMI I am connected to SONY STR-DH520

Does that statement mean we are now on to a different problem?

I can play audio through an HDMI connection from my Nvidia GT216 to a digital TV - Sharp LC-24DV250K. And I can do this on both Ubuntu 15.04 and wily werewolf (15.10)

Sound Settings now gives an Output of HDMI/DisplayPort2 and on my system it adds GT216 HDMI Audio Controller. But we do have to select it.

I use wily werewolf every day and it is very stable but I was not sure if 15.04 allowed audio through HDMI. So, I especially loaded Ubuntu 15.04 to check. You should be able to use an HDMI video connection to the graphic adapter and get audio through the speakers of the TV. You use the TV remote to control the volume level.

If the volume level in the sound indicator applet is set too low we will not hear any sound. 

Regards.

---

### Post by kubanc on 2015-07-04
> **grahammechanical said:**
> Does that statement mean we are now on to a different problem?

I can play audio through an HDMI connection from my Nvidia GT216 to a digital TV - Sharp LC-24DV250K. And I can do this on both Ubuntu 15.04 and wily werewolf (15.10)

Regards.

OK, but you are sending audio and video through graphic card.
My audio HDMI connection goes from motherboard.

If I need to open a new thread for HDMI audio problem let me know and I will do it, 
Thank you

---

### Post by Yellow Pasque on 2015-07-04
> **kubanc said:**
> My audio HDMI connection goes from motherboard.

So you're trying to send audio through HDMI from a GPU you're not using? I don't think you can do that.

---

### Post by kubanc on 2015-07-06
> **Temüjin said:**
> So you're trying to send audio through HDMI from a GPU you're not using? I don't think you can do that.

What do you mean by that I am not using it?

I was using that HDMI audio on previous releases of Ubuntu and it worked fine

---

### Post by Yellow Pasque on 2015-07-06
> **kubanc said:**
> What do you mean by that I am not using it?
You are not using your motherboard's GPU because of the 550. I didn't think you could use HDMI audio from a port belonging to a GPU not in use, but I could be wrong.
Anyway, get more info on it: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by kubanc on 2015-07-06
> **Temüjin said:**
> You are not using your motherboard's GPU because of the 550. I didn't think you could use HDMI audio from a port belonging to a GPU not in use, but I could be wrong.
Anyway, get more info on it: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

So, you are saying that I cannot send audio through HDMI because I am using graphic card 550ti and I am not sending video through my integrated motherboard graphic card?

But in my previous versions this worked. The only thing that was wrong is, that from time to time it did not recognize HDMI, but when I restarted the computer HDMI was found.

---

### Post by Yellow Pasque on 2015-07-06
Well, then I'm wrong on that. Still, more info needed: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Tsahre on 2015-07-07
I had the same problem before. It was resolved by uninstalling and reinstalling the drivers.

---

### Post by kubanc on 2015-07-13
Temüjin, alsainfo:
[http://www.alsa-project.org/db/?f=1593223db5c78dc14dbc11e04521268990743f21](http://www.alsa-project.org/db/?f=1593223db5c78dc14dbc11e04521268990743f21)

What drivers did you uninstall and reinstall Tsahre?

---

