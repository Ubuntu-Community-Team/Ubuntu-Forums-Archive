---
title: "Help with kernel update"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by superstoffer on 2009-07-07
Hello everybody,

I've tried to install VirtualBox 3.0, but I get the following error when installing:
Unable to find a precompiled module for the current kernel!

Without a suitable kernel module you will not be able to start any VMs.
It is strongly recommended to compile a kernel module now. The kernel
headers and the tools to build kernel modules (gcc, make, binutils, ...) 
are required. However if you know that a suitable kernel module already 
exists at another location, you might want to override the default by     
setting KDIR=<full_path_to_vboxdrv_module> in /etc/default/virtualbox.

What do I do?

Edit:

I think I need to get new kernel, but how do I do that?

---

### Post by starcraft.man on 2009-07-07
If your running anything past 8.04, I'm pretty sure you meet requirements. No, this error is because you lack the build-essential package, which, is required for the modification of your current kernel to run the modules from Vbox. 

To install, open a terminal (Applications > Accessories )and then type and run the fllowing:

```
sudo apt-get install build-essential
```

Once complete, run installation again. I assume your using the repos from [here ]("http://www.virtualbox.org/wiki/Linux_Downloads")yes? It's preferably to install from them rather than just the packages.

Also, you may be pestered by a message after install that says "You must run /etc/init.d/vboxdrv setup in a terminal after installation" or such. Just run the command in the terminal you just opened with sudo power.

```
sudo /etc/init.d/vboxdrv setup
```

Reboot the PC after all done and everything should be fine. Enjoy vbox.

---

### Post by superstoffer on 2009-07-07
Thanks for the quick reply!

I get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 8707kB of archives.
After this operation, 34.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main linux-libc-dev 2.6.24-22.45 [699kB]
Get: 2 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main libc6-dev 2.7-10ubuntu4 [3344kB]
Get: 3 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main libstdc++6-4.2-dev 4.2.4-1ubuntu3 [1187kB]
Get: 4 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main g++-4.2 4.2.4-1ubuntu3 [2784kB]
Get: 5 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Get: 6 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get: 7 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/main patch 2.5.9-4 [95.6kB]
Get: 8 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get: 9 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/main build-essential 11.3ubuntu1 [7066B]
Fetched 8707kB in 2s (4285kB/s)   
Selecting previously deselected package linux-libc-dev.
(Reading database ... 160449 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-22.45_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-libc-dev (2.6.24-22.45) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up libstdc++6-4.2-dev (4.2.4-1ubuntu3) ...
Setting up g++-4.2 (4.2.4-1ubuntu3) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by starcraft.man on 2009-07-07
Same terminal:

```
sudo apt-get install -f
```

I think it otherwise installed fine, above command goes over and fixes any broken packages/errors.

---

### Post by superstoffer on 2009-07-07
Now I get the following (I am new to Linux, so i apologize if something should be obvious):

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by starcraft.man on 2009-07-07
Persistent, this isn't a big problem, the ACPI package really just is your advanced power features like suspend and hibernate. Not necessary to daily function, can you continue as I said above, virtual box should install fine.

As to this problem, I'm a bit uncertain. I think I'd try reinstalling it, but there might be some underlying hardware support problem. Has this been happening since you installed?

Try:
```
sudo apt-get autoremove
```

and then:
```
sudo apt-get --reinstall install acpid
```

You might be best served by creating a new thread saying there's ACPI trouble (assuming the following doesn't work), and listing the relevant information (including hardware information on computer) and link back here to show the problem. I don't think I can help you further, I've answered how to install vbox properly and done my best with the ACPI trouble.

---

### Post by superstoffer on 2009-07-07
Oh thank you very much for your help! When I get this acpi-problem fixed, I know how to install vbox...
I think I will start a new thread as you suggest....

---

