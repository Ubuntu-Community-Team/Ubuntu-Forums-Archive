---
title: "Problems With ATI Drivers in kubuntu"
date: 2009-05-20
forum: Hardware
---

### Post by apamix on 2009-05-20
Hi all i have HP Pavilion dv5000 with kubuntu 9.04 
I have problems to install my ATI Radeon Xpress 200M 

I try to install my drivers by this way 

sudo gedit /etc/X11/xorg.conf and add these lines at the end of the file: 
    [SIZE=-1]**File:** /etc/X11/xorg.conf[/SIZE]    Section "Extensions"
        Option  "Composite" "Disable"
EndSection  sudo gedit /etc/default/linux-restricted-modules-common Edit *DISABLED_MODULES* to include fglrx 
    [SIZE=-1]**File:** /etc/default/linux-restricted-modules-common[/SIZE]    DISABLED_MODULES="fglrx"  ** Installing the new driver **

sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
*Create .deb packages:* 
 sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.30.3.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
*Install .deb packages:* 
 sudo dpkg -i xorg-driver-fglrx_8.30.3-1*.deb
sudo dpkg -i fglrx-kernel-source_8.30.3-1*.deb
sudo dpkg -i fglrx-control_8.30.3-1*.deb
*Remove any old fglrx debs from /usr/src/:* 
 sudo rm /usr/src/fglrx-kernel*.deb
*Compile the kernel module:* 
 sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
**IMPORTANT**: You have to recompile the kernel module after each kernel update! 
*Update the xorg.conf file:* 
 sudo aticonfig --initialsudo aticonfig --overlay-type=Xv
**Note:** You could also edit your */usr/X11/xorg.conf* file to change your driver to **fglrx** then run: 
 sudo aticonfig --overlay-type=Xv
This way your *xorg.conf* file will stay clean. 
*Now Reboot:* 
 sudo shutdown -r now

But when i go to 
dpkg -i fglrx-kernel-source_8.593-0ubuntu1_i386.deb

i get 

Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.29.2-apamix (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.593/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.29.2-apamix (i686) first.

---

