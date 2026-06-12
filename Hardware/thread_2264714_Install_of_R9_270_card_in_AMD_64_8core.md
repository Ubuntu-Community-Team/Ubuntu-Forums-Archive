---
title: "Install of R9 270 card in AMD 64 8core"
date: 2015-02-09
forum: Hardware
---

### Post by fjstjohn2 on 2015-02-09
Hello,

I recently have been struggling to get the closed source drivers installed for the AMD R9 graphics card that my computer came with. The open source drivers work great, but I'm looking into using the streaming processors for parallel processing tasks (BEAST/Beagle software) and use of OpenCL and therefore the proprietary drivers (Catalyst) are recommended.  As it stands, with the open source drivers, the Beagle software does not see the R9 stream processors, only CPU0.

The install support provided by the Beagle lib install page (**[https://code.google.com/p/beagle-lib/wiki/LinuxInstallInstructions](https://code.google.com/p/beagle-lib/wiki/LinuxInstallInstructions)**) was very clear, but when I started installing the ADM catalyst drivers I ran into curious problems.  Basically, no matter what guide I follow, whether it be the Ubuntu documentation ([https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)), the AMD documentation ([http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx)) or the method through the wiki of the unofficial AMD linux community ([http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide)) I ran into problems.

The AMD information really lead to a dead end because the instructions are based on downloading or otherwise obtaining a file with a .run extension while the only file obtainable through the AMD Catalyst web site is a .deb installation file which can be used in Ubuntu Software Center or on the command line. Following the (really very nice) guide from the unofficial AMD linux community (see above) provided a very similar result (see output below) as when using the AMDdriver.deb file in the Ubuntu Software Center or by following the Ubuntu documentation guide. Similar to the results pasted below the Ubuntu Software Center sates that the .deb file has "fglrx-core" as a dependency, but is not satisfiable. Ouch! simple searches for the fglrx-core file were not successful. The way I interpret the issue is that installation of the Catalyst driver requires installation of the Catalyst driver first. Ha?

Any help would be appriceated

...............................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/trusty
Package /home/fjstjohn/catalyst14.12/fglrx-core_14.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/fjstjohn/catalyst14.12/fglrx_14.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/fjstjohn/catalyst14.12/fglrx-dev_14.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/fjstjohn/catalyst14.12/fglrx-amdcccle_14.501-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.n3sv3m
fjstjohn@fsj-8c:~/catalyst14.12$ sudo dpkg -i fglrx*.deb
Selecting previously unselected package fglrx.
(Reading database ... 474588 files and directories currently installed.)
Preparing to unpack fglrx_14.501-0ubuntu1_amd64.deb ...
Unpacking fglrx (2:14.501-0ubuntu1) ...
Selecting previously unselected package fglrx-amdcccle.
Preparing to unpack fglrx-amdcccle_14.501-0ubuntu1_amd64.deb ...
Unpacking fglrx-amdcccle (2:14.501-0ubuntu1) ...
Selecting previously unselected package fglrx-core.
dpkg: regarding fglrx-core_14.501-0ubuntu1_amd64.deb containing fglrx-core:
 fglrx-core conflicts with libopencl1
  ocl-icd-libopencl1:amd64 provides libopencl1 and is present and installed.

dpkg: error processing archive fglrx-core_14.501-0ubuntu1_amd64.deb (--install):
 conflicting packages - not installing fglrx-core
Selecting previously unselected package fglrx-dev.
Preparing to unpack fglrx-dev_14.501-0ubuntu1_amd64.deb ...
Unpacking fglrx-dev (2:14.501-0ubuntu1) ...
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on fglrx-core; however:
  Package fglrx-core is not installed.

dpkg: error processing package fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.

dpkg: error processing package fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx-core | fglrx; however:
  Package fglrx-core is not installed.
  Package fglrx is not configured yet.

dpkg: error processing package fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Errors were encountered while processing:
 fglrx-core_14.501-0ubuntu1_amd64.deb
 fglrx
 fglrx-amdcccle
 fglrx-dev

---

### Post by Yellow Pasque on 2015-02-09
```
fglrx-core conflicts with libopencl1
ocl-icd-libopencl1:amd64 provides libopencl1 and is present and installed.
```

Did you try this? [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#fglrx-core_conflicts_with_libopencl1](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#fglrx-core_conflicts_with_libopencl1)

---

### Post by QIII on 2015-02-09
Hey!  That's a great tip.  Having spent the entire weekend testing an R9 290X provided by Canonical, I had not run into that since I don't use Wine.  I'll reference that with a link in my write-up and when I do some updates to the community wiki.

---

### Post by fjstjohn2 on 2015-02-09
Yes it worked.  Thanks Temujin.[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")

---

