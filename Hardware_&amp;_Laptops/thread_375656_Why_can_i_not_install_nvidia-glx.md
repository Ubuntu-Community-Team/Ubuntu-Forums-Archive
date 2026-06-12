---
title: "Why can i not install nvidia-glx"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by Jphenow on 2007-03-04
When i go to adept manager it says there are problems and this the output from when i try sudo apt-get install...

[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java ksig ktip python-pexpect atlantikdesigner python-pycurl
  kpager liblog4j1.2-java libseda-java libcommons-cli-java noatun-plugins
  libgtk-jni tidy libtidy-0.99-0 libdb4.3++c2 python-rpm libbcprov-java
  kaddressbook-plugins libcrypto++5.2c2a libgtk-java kdelibs kate-plugins
  kdeaddons-kfile-plugins
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
(Reading database ... 217021 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.7-11.2_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.7-11.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.7-11.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/I]

any ideas??

---

### Post by kerry_s on 2007-03-04
Use synaptic instead, use the run command, type kdesu synaptic, click reload than try.

If you use the command line, you need to start with "sudo apt-get update" first.

---

### Post by Jphenow on 2007-03-04
i've done that a bunch

---

### Post by Jphenow on 2007-03-04
i got nearly same output from that...Sub-process error, exit status 2 or somethin, i think i might have mesa stuff left over that shouldn't be, what mesa stuff do un-install if i do have some?

---

### Post by kerry_s on 2007-03-04
Sounds like your synaptic is borked, looks like from the error above you switched from fglrx to nvidia, but you never completely removed fglrx.
Have you already tried running-> sudo apt-get -f install

---

### Post by Jphenow on 2007-03-04
oh man i figured it out, after i put that card in i had trouble getting back into the desktop at all and didn't realize my bro had done the manual install for it through wget, so sorry bout all that guys, i already had it installed =\

---

### Post by kraymore on 2007-08-30
i get the same error codes when using the alternate cd of feisty.  i'm going to venture to guess that it doesn't happen with the non-debian installer feisty.  i wish i could get it to work with the alternate cd so i wouldn't have to use envy to install the drivers.

---

