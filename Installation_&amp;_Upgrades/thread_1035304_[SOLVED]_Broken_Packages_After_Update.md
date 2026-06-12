---
title: "[SOLVED] Broken Packages After Update"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by gmjs on 2009-01-09
Hi,

I'm running Ubuntu 8.04.1 and have had problems with the last two updates.

After the first update, the packages m4 and gettext became broken, and dpkg takes great delight in telling me this every time I use it to install another application!  All updates and other applications I have tried to install from the repositories have all installed OK though.

The second time I ran the software update, the updates failed and package util-linux is now "Broken" too.  It fails during the prerm script, as (I believe) do the other two.

Is there anything I've done to cause this?  I may have installed m4 from source when compiling another application at some point.  I'm assuming this has something to do with it!

Can I solve this problem without reinstalling Ubuntu?

Configuring all packages returns an error stating that the package util-linux has "very bad inconsistencies" and should be reinstalled before configuring.  The package will not, however, be reinstalled.

```
**$ graham@asus:~$ sudo apt-get -u upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
The following packages will be upgraded:
  bind9-host bsdutils dnsutils libbind9-30 libdns35 libisc35 libisccc30
  libisccfg30 liblwres30 linux-libc-dev linux-restricted-modules-common
  nautilus-share util-linux-locales xorg-driver-fglrx
14 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
3 not fully installed or removed.
Need to get 0B/11.8MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up util-linux (2.13.1-5ubuntu3) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing util-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
**$ graham@asus:~$ sudo aptitude**
[I]
[ Presses g g ][/I]

(Reading database ... 140657 files and directories currently installed.)
Removing gettext ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing m4 ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing m4 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gettext
 m4
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.
```

Many thanks for any help,

Graham

---

### Post by namdung on 2009-01-09
In Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

Fix broken packages in *Synaptic Package Manager==>Custom Filters==>Broken*

---

### Post by gmjs on 2009-01-09
Thanks for the reply.

I've used **dpkg --configure -a** a couple of times, but it doesn't help.

Synaptic doesn't think there are any broken packages and reports they have been fixed.

Installation of m4, gettext and util-linux still fail.

```
**graham@asus:~$ sudo aptitude reinstall m4**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libdns35 libisc35 linux-libc-dev linux-restricted-modules-common 
The following packages have been kept back:
  bind9-host bsdutils dnsutils libbind9-30 libisccc30 libisccfg30 
  liblwres30 linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic nautilus-share util-linux-locales 
  xorg-driver-fglrx 
The following packages will be REINSTALLED:
  m4 
The following partially installed packages will be configured:
  gettext util-linux 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 18 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up util-linux (2.13.1-5ubuntu3) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing util-linux (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gettext (0.17-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
Setting up m4 (1.4.10-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
 gettext
 m4
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by gmjs on 2009-01-11
Hi,

I haven't had much luck in trying to solve this.  Before I reinstall (and back up this time #-o) does anyone know why the program **install-info** program fails while running the post-installation scripts for the three packages?  It seems to be expecting a second parameter, but I don't follow what it does so can't see why.

```
Setting up util-linux (2.13.1-5ubuntu3) ...
**install-info: No dir file specified; try --help for more information.**
dpkg: error processing util-linux (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gettext (0.17-2ubuntu1) ...
**install-info: No dir file specified; try --help for more information**.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
Setting up m4 (1.4.10-1) ...
**install-info: No dir file specified; try --help for more information.**
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
 gettext
 m4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'll reinstall and mark as [SOLVED] after this post!

Many thanks,

Graham

---

### Post by KramAri on 2010-07-31
I am having the same error I believe.


/usr/share/debconf/frontend: 8: Syntax error: "(" unexpected
dpkg: error processing sane-utils (--configure):
 subprocess installed post-installation script returned error exit status 2
 just one of many on screen after doing sudo dpkg --configure -a

Any suggestions?

---

