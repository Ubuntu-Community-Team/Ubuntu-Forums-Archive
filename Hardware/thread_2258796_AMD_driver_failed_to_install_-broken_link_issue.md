---
title: "AMD driver failed to install -broken link issue?"
date: 2014-12-30
forum: Hardware
---

### Post by Handssolow on 2014-12-30
I get these messages in the terminal when the AMD driver fails to install-

forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken 

We have here a 6 core AMD desktop with a Radeon HD7950, which was running Ubuntu 12.04 LTS for general use, viewing Google Earth, some PlayonLinux games (mostly Oblivion) and a dos based game. I'd managed to install an AMD driver a while back despite jtk-jockey been broken. On 22 December 2014 update manager broke a previously usable system. Part of the record-

Install: fglrx-amdcccle-updates:amd64 (13.350.1-0ubuntu0.0.1), linux-headers-3.2.0-74:amd64 (3.2.0-74.109), fglrx-updates:amd64 (13.350.1-0ubuntu0.0.1, automatic), linux-headers-3.13.0-43:amd64 (3.13.0-43.72~precise1), linux-headers-3.2.0-74-generic:amd64 (3.2.0-74.109), fglrx-updates-dev:amd64 (13.350.1-0ubuntu0.0.1), linux-image-3.13.0-43-generic:amd64 (3.13.0-43.72~precise1), linux-headers-3.13.0-43-generic:amd64 (3.13.0-43.72~precise1)

End result, no Google Earth, no PlayonLinux Oblivion game, though the dos game still worked. After attempts to reinstalling the fglrx drivers got me nowhere, I decided to upgrade to 14.04 LTS and got into further problems. I had a normal login screen, input of the password left a blank screen save for our normal desktop wallpaper. CTRL+ALT+F1 to a text login was the best on offer. After a few hours wrongly thinking that the failure to login was a file permissions issue, an uninstall of fglrx etc eventually produced a normal login and GUI.

I've had no success installing a current AMD driver either through Additional Drivers, Synaptic, the AMD installer, installing created packages or an edited created package (see below). I'm always thrown back onto Mesa when the AMD Driver doesn't install. Others have reported similar experiences.

[http://askubuntu.com/questions/558520/cannot-install-new-omega-driver-from-amd](http://askubuntu.com/questions/558520/cannot-install-new-omega-driver-from-amd)
[https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1376587](https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1376587)
[http://askubuntu.com/questions/540780/14-10-wine-and-fglrx-conflict](http://askubuntu.com/questions/540780/14-10-wine-and-fglrx-conflict)

I've made no progress after many hours.
Any suggestions?

---

### Post by Handssolow on 2014-12-31
Further attempts to install the AMD 14.501 have met with no success either. Mesa as ever but at least a working GUI but son not happy as his PlayonLinux games no longer work. They did before the December's updates to 12.04LTS.

I've been following advice here and applying the recommended modification to resolve the fglrx Wine conflicts.
  
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE)

The failure to build error is logged in /Var/lib/dkms/fglrx-core/14.501/build/make.log

DKMS make.log for fglrx-core-14.501 for kernel 3.13.0-43-generic (x86_64) 
Wed Dec 31 09:09:42 GMT 2014 
/usr/sbin/dkms: line 73: cd: /var/lib/dkms/fglrx/14.501/build: No such file or directory 
make.sh: 1: make.sh: gcc: not found 
make.sh: 42: [: !=: unexpected operator 
AMD kernel module generator version 2.1 
doing Makefile based build for kernel 2.6.x and higher 
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers 
make -C /lib/modules/3.13.0-43-generic/build SUBDIRS=/var/lib/dkms/fglrx-core/14.501/build/2.6.x modules 
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-43-generic' 
/usr/src/linux-headers-3.13.0-43-generic/arch/x86/Makefile:98: stack protector enabled but no compiler support 
/usr/src/linux-headers-3.13.0-43-generic/arch/x86/Makefile:113: CONFIG_X86_X32 enabled but no binutils support 
make[1]: gcc: Command not found 
  CC [M]  /var/lib/dkms/fglrx-core/14.501/build/2.6.x/firegl_public.o 
/bin/sh: 1: gcc: not found 
make[2]: *** [/var/lib/dkms/fglrx-core/14.501/build/2.6.x/firegl_public.o] Error 127 
make[1]: *** [_module_/var/lib/dkms/fglrx-core/14.501/build/2.6.x] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-43-generic' 
make: *** [kmod_build] Error 2 
build failed with return value 2

I am not sure about the meaning of this line-
/usr/sbin/dkms: line 73: cd: /var/lib/dkms/fglrx/14.501/build: No such file or directory

Does it refer to line 73 in /usr/sbin/dkms ? which is
(eval "$1" >/dev/null 2>&1; echo "exitval=$?" >> "$exitval_file") &

When I look in /var/lib/dkms/fglrx/14.501/build there are loads of files

I am at a loss and at the limits of my experience.

Edit:
Found another report of something similar dated 21st December 2014 though kernel version perhaps at limit of AMD's support-
[http://askubuntu.com/questions/563922/amd-omega-drivers-dont-work-with-kernel-3-17-6-on-trusty](http://askubuntu.com/questions/563922/amd-omega-drivers-dont-work-with-kernel-3-17-6-on-trusty)

Here uname -r shows 3.13.0-43-generic which is within AMD's kernel support

---

### Post by Handssolow on 2015-01-08
Not much progress to report, I've had no success installing AMD's Omega graphics driver.
I did manage to get working again a couple of games, Oblivion and Stalker, by changing up to Wine 1.7 in PlayOnLinux. The open source Mesa driver is no match for the AMD 13.1 experimental driver we'd previously used until December 2014's 12.04 updates.
It replaced a perfectly good fglrx driver for one which didn't work. Without a working AMD driver, my son's view is that these games are unplayable.
The likelihood that he'd run a computer of his own in the future running Ubuntu is next to zero.

---

### Post by Handssolow on 2015-01-09
It's not all bad news here.
I reinstalled the gcc package which a earlier log message had pointed to. However, after another failed attempt at an install of the Omega driver (using a modified fglrx-core to avoid the conflicts with libopencl1 because of Wine), I followed the wiki advice here-
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide)

"If you plan on using open-source drivers, you will need to reinstall some packages because Catalyst overwrites or diverts some key 3D libraries with proprietary versions" 

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati

A reboot yielded a workable mesa open source driver giving acceptable game play with Oblivion and  Stalker which my son reports to be down by about 15% on the previous AMD Catalyst 13.1 experimental.

Edit: I have added today's terminal output from failed install of the AMD driver

~/catalyst14.12$ sudo dpkg -i fglrx*.deb 
Selecting previously unselected package fglrx. 
(Reading database ... 316911 files and directories currently installed.) 
Preparing to unpack fglrx_14.501-0ubuntu1_amd64.deb ... 
Unpacking fglrx (2:14.501-0ubuntu1) ... 
Selecting previously unselected package fglrx-amdcccle. 
Preparing to unpack fglrx-amdcccle_14.501-0ubuntu1_amd64.deb ... 
Unpacking fglrx-amdcccle (2:14.501-0ubuntu1) ... 
Selecting previously unselected package fglrx-core. 
Preparing to unpack fglrx-core_14.501-0ubuntu1_amd64.deb ... 
Unpacking fglrx-core (2:14.501-0ubuntu1) ... 
Selecting previously unselected package fglrx-dev. 
Preparing to unpack fglrx-dev_14.501-0ubuntu1_amd64.deb ... 
Unpacking fglrx-dev (2:14.501-0ubuntu1) ... 
Setting up fglrx-core (2:14.501-0ubuntu1) ... 
update-alternatives: using /usr/lib/fglrx-core/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GFXCORE.conf (x86_64-linux-gnu_gfxcore_conf) in auto mode 
Loading new fglrx-core-14.501 DKMS files... 
Building only for 3.13.0-43-generic 
Building for architecture x86_64 
Building initial module for 3.13.0-43-generic 
Done. 

fglrx: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/ 

depmod..... 

DKMS: install completed. 
update-initramfs: deferring update (trigger activated) 
Setting up fglrx-dev (2:14.501-0ubuntu1) ... 
Setting up fglrx (2:14.501-0ubuntu1) ... 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken 
Processing triggers for ureadahead (0.100.0-16) ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... 
Setting up fglrx-amdcccle (2:14.501-0ubuntu1) ... 
Processing triggers for mime-support (3.54ubuntu1.1) ... 
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
Processing triggers for initramfs-tools (0.103ubuntu4.2) ... 
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic 
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...

---

