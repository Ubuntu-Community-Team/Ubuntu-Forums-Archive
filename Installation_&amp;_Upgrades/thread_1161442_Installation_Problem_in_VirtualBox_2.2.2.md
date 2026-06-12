---
title: "Installation Problem in VirtualBox 2.2.2"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by anuraggautam on 2009-05-16
Hi All ,

I am receiving below pasted problem while installing VirtualBox in my Ubuntu 8.04

Do you know how to solve this problem ?


---- Starts From Here -----

root@Anurag-Laptop:/home/anurag# apt-get install virtualbox-2.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgalago1.0-cil libxalan110 libgalago3 libwv-1.2-3 beagle
  virtualbox-ose-modules-2.6.24-21-generic cabextract libgsf0.0-cil
  libxerces27
Use 'apt-get autoremove' to remove them.
Recommended packages:
  dkms libsdl-ttf2.0-0
The following NEW packages will be installed:
  virtualbox-2.2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 43.9MB of archives.
After this operation, 92.0MB of additional disk space will be used.
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) hardy/non-free virtualbox-2.2 2.2.2-46594_Ubuntu_hardy [43.9MB]
Get:2 [http://download.virtualbox.org](http://download.virtualbox.org) hardy/non-free virtualbox-2.2 2.2.2-46594_Ubuntu_hardy [43.9MB]
Fetched 37.9MB in 45min47s (13.8kB/s)                                           
Preconfiguring packages ...
(Reading database ... 255121 files and directories currently installed.)
Unpacking virtualbox-2.2 (from .../virtualbox-2.2_2.2.2-46594%5fUbuntu%5fhardy_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/virtualbox-2.2_2.2.2-46594%5fUbuntu%5fhardy_i386.deb (--unpack):
 trying to overwrite `/lib/modules/2.6.24-23-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-23-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-2.2_2.2.2-46594%5fUbuntu%5fhardy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



---Ends ----

Hope for the Quick Reply :-)

Regards,

---

### Post by mikewhatever on 2009-05-16
Try running **sudo apt-get autoremove** before installing. Removing any other version of Virtualbox might also help.

---

### Post by anuraggautam on 2009-05-17
> **mikewhatever said:**
> Try running **sudo apt-get autoremove** before installing. Removing any other version of Virtualbox might also help.

This couldn't help me .....I am not able to install Virtual Box after running above mentioned command.

I am receiving same error after installing the package.Please help me to sort out this thing.

Regards,

---

### Post by anuraggautam on 2009-05-17
> **anuraggautam said:**
> This couldn't help me .....I am not able to install Virtual Box after running above mentioned command.

I am receiving same error after installing the package.Please help me to sort out this thing.

Regards,

Solved after Uninstalling all previous version of VirtualBox.

---

### Post by RogerThat on 2009-06-06
I am also having problems upgrading VirtualBox.  I had VirtualBox 2.0 installed.  I tried installing VB 2.2.4, from the VirtualBox.org website, but the GDebi package manager complained that VirtualBox 2.0 conflicted with the new version, so it would not install the new version.  I being somewhat less than fully alert, due to my meds, decided that I would just delete the old software, which I did by going into several directories and deleting files.  GDebi still complained, and wouldn't install the new version.  I found the dpkg --help commmand, and did a "sudo dpkg --purge virtualbox", which I hoped would get rid of the entry in whatever database dpkg is using.  This was only somewhat helpful.  I now get a package is not installed when I run the dpkg --purge virtualbox command again, but doing the dpkg --install virtualbox-2.2_2.2.4 command gives and error that says virtualbox is still installed.  I seem to be in a tight loop here, with no easy way out.  Anybody have any ideas?
Thanks, Roger

---

