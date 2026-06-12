---
title: "Hardy heron restricted driver problem"
date: 2008-05-09
forum: Hardware
---

### Post by darkhorse186 on 2008-05-09
Hi,
I recently upgraded to Hardy heron and there is a problem with the restricted drivers. before in 7.10 i just had to enable the restricted driver for my graphics card but now on the restricted drivers panel my graphics card doesn't show up. I've tried programs like EnvyNG but that just caused there to be a problem booting and i had to uninstall it. The driver used to work fine.
Does anyone know of a way to fix his

---

### Post by werries on 2008-05-09
I had two thoughts, both which may be wrong.

first of all, i'm not sure how releases go, but is there any problem with your graphics not working? have you tried enabling the extra effects for the desktop, cause if they just work there might have been an open source driver made. and if not, it should try and bring up a menu for restricted drivers, and maybe offer to download something, such as "nvidia-glx". 

any chance you know what graphics card you have?

---

### Post by darkhorse186 on 2008-05-10
The desktop effects can't be enabled for some reason.
I have a nvidia geforce fx5200

---

### Post by maramot on 2008-05-10
Open the synaptic package manager (System->Administration->Synaptic package manager and make sure you have a package installed called nvidia-glx-new. If you have that installed, you should have the proprietary "NVIDIA accelerated graphics driver (latest cards)" listed in your System->Administration->Hardware Drivers applet.

Do you have that package installled?

If you don't see your video card driver in that applet the problem may be that your driver has somehow been added to the "blacklist" file. You'll have to open up the blacklist and see if it's there. here's the method I'd use: type "sudo mc" in the terminal. After you type in your password, you'll launch Midnight Commander, with root permissions on editing files. Navigate to your /etc/modprobe.d directory, and open "blacklist" for editing. See if it has any lines relevant to or containing "nvidia"

---

### Post by mrjobson on 2008-05-10
I ahve this problem too. It refuses to install:

 apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5249kB of archives.
After this operation, 15.6MB of additional disk space will be used.
(Reading database ... 148487 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/nvidia/libglx.so.xserver-xorg-core' with
  different file `/usr/lib/xorg/modules/extensions/libglx.so', not allowed
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by darkhorse186 on 2008-05-10
Hi,
I have that package installed and it still doesn't show up. I have checked the blacklist file and there doesn't appear to be anything related to nvidia there but in the file "blacklist-local" it says "blacklist nvidia-new"

---

### Post by maramot on 2008-05-12
Did you try removing it? I'm not exactly sure what's the "local" part for in blaclist-local though...?

---

### Post by darkhorse186 on 2008-05-15
Yes but that didn't work

---

