---
title: "Ati Catalyst 11.8 doesn't seem to install properly"
date: 2011-09-17
forum: Hardware
---

### Post by timuckun on 2011-09-17
Trying to install the drivers from the ATI 

cd ~/; mkdir catalyst11.8; cd catalyst11.8/
$ wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run)

[edit] Create .deb packages.

$ sh ./ati-driver-installer-11-8-x86.x86_64.run --buildpkg Ubuntu/natty

[edit] Install .debs.

$ sudo dpkg -i fglrx*.deb

[edit] Generate a new /etc/X11/xorg.conf file

Unfortunately, there is no sure way to generate the ATI version of the Xorg.conf file. It is entirely dependent on your configuration. The following subsections will attempt to address possible (and tested) variations for their respective configurations.
[edit] Generic Config

This will work for most people:

$ sudo aticonfig --initial -f

This doesn't work. The output is 

Unable to open /etc/ati/control, please reinstall the driver.
/usr/lib/fglrx/bin/aticonfig: No supported adapters detected



The output of the install is 


dpkg -i *.deb
(Reading database ... 174335 files and directories currently installed.)
Preparing to replace fglrx 2:8.881-0ubuntu1 (using fglrx_8.881-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx ...
Preparing to replace fglrx-amdcccle 2:8.881-0ubuntu1 (using fglrx-amdcccle_8.881-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-dev 2:8.881-0ubuntu1 (using fglrx-dev_8.881-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-dev ...
Setting up fglrx (2:8.881-0ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/mesa/ld.so.conf because link group gl_conf is broken.
Loading new fglrx-8.881 DKMS files...
Building only for 2.6.38-11-generic-pae
Building for architecture i686
Building initial module for 2.6.38-11-generic-pae
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-11-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_NZ.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.881-0ubuntu1) ...
Setting up fglrx-dev (2:8.881-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

---

