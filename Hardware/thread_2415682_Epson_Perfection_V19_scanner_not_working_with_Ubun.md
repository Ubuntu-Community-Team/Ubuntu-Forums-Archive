---
title: "Epson Perfection V19 scanner not working with Ubuntu 18.04"
date: 2019-03-29
forum: Hardware
---

### Post by Joe_Linux on 2019-03-29
Tried using My Epson Perfection V19 scanner in Ubuntu 18.04 (it worked under Ubuntu 16.04). It seems to be recognized under Xsane. When I try to scan the message " Failed to start scanner operation was canceled". Even tried running it as root no change in error message. sudo: sane: command not found
joe@joe-X555LAB:~$ sudo xsane
Gtk-Message: 14:16:33.952: Failed to load module "canberra-gtk-module"
joe@joe-X555LAB:~$ sudo apt install libcanberra-gtk-module libcanberra-gtk3-module
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcanberra-gtk3-module is already the newest version (0.30-5ubuntu1).
libcanberra-gtk3-module set to manually installed.
The following packages were automatically installed and are no longer required:
  app-install-data apt-xapian-index cfortran comerr-dev fonts-freefont-otf
  g++-5 krb5-multidev libafterimage0 libboost-filesystem1.58.0
  libboost-program-options1.58.0 libboost-system1.58.0 libftgl2 libgl2ps-dev
  libgl2ps1.4 libgnome-keyring-common libgnome-keyring0 libgssrpc4
  libkadm5clnt-mit11 libkadm5srv-mit11 libkdb5-9 libkrb5-dev libnih-dbus1
  libssl-dev libssl-doc libvte-common libvte9 libxpm-dev par2 python-apt
  python-aptdaemon python-aptdaemon.gtk3widgets python-asn1crypto python-attr
  python-automat python-blinker python-cairo python-cffi-backend python-click
  python-colorama python-constantly python-cryptography python-cups
  python-dbus python-debian python-defer python-dirspec python-enum34
  python-gi python-gi-cairo python-glade2 python-gobject-2 python-gtk2
  python-httplib2 python-hyperlink python-idna python-incremental
  python-ipaddress python-jwt python-oauthlib python-openssl python-pam
  python-piston-mini-client python-pyasn1 python-serial python-twisted-bin
  python-vte python-xapian python-xdg python-zope.interface
  python3-piston-mini-client python3-xapian software-center-aptdaemon-plugins
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libcanberra-gtk-module libcanberra-gtk0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.9 kB of archives.
After this operation, 84.0 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 libcanberra-gtk0 amd64 0.30-5ubuntu1 [7,864 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 libcanberra-gtk-module amd64 0.30-5ubuntu1 [10.0 kB]
Fetched 17.9 kB in 1s (26.1 kB/s)                 
Selecting previously unselected package libcanberra-gtk0:amd64.
(Reading database ... 203248 files and directories currently installed.)
Preparing to unpack .../libcanberra-gtk0_0.30-5ubuntu1_amd64.deb ...
Unpacking libcanberra-gtk0:amd64 (0.30-5ubuntu1) ...
Selecting previously unselected package libcanberra-gtk-module:amd64.
Preparing to unpack .../libcanberra-gtk-module_0.30-5ubuntu1_amd64.deb ...
Unpacking libcanberra-gtk-module:amd64 (0.30-5ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up libcanberra-gtk0:amd64 (0.30-5ubuntu1) ...
Setting up libcanberra-gtk-module:amd64 (0.30-5ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ... 
When I tried running Xsane as root I received the message "Failed to load module "canberra-gtk-module"" So I tried loading the module as you might see above still no change. Any help might be appreciated.

---

### Post by nlona on 2019-03-30
> **Joe_Linux said:**
> Tried using My Epson Perfection V19 scanner in Ubuntu 18.04 (it worked under Ubuntu 16.04). It seems to be recognized under Xsane. When I try to scan the message " Failed to start scanner operation was canceled". Even tried running it as root no change in error message. sudo: sane: command not found
joe@joe-X555LAB:~$ sudo xsane
Gtk-Message: 14:16:33.952: Failed to load module "canberra-gtk-module"
joe@joe-X555LAB:~$ sudo apt install libcanberra-gtk-module libcanberra-gtk3-module
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcanberra-gtk3-module is already the newest version (0.30-5ubuntu1).
libcanberra-gtk3-module set to manually installed.
The following packages were automatically installed and are no longer required:
  app-install-data apt-xapian-index cfortran comerr-dev fonts-freefont-otf
  g++-5 krb5-multidev libafterimage0 libboost-filesystem1.58.0
  libboost-program-options1.58.0 libboost-system1.58.0 libftgl2 libgl2ps-dev
  libgl2ps1.4 libgnome-keyring-common libgnome-keyring0 libgssrpc4
  libkadm5clnt-mit11 libkadm5srv-mit11 libkdb5-9 libkrb5-dev libnih-dbus1
  libssl-dev libssl-doc libvte-common libvte9 libxpm-dev par2 python-apt
  python-aptdaemon python-aptdaemon.gtk3widgets python-asn1crypto python-attr
  python-automat python-blinker python-cairo python-cffi-backend python-click
  python-colorama python-constantly python-cryptography python-cups
  python-dbus python-debian python-defer python-dirspec python-enum34
  python-gi python-gi-cairo python-glade2 python-gobject-2 python-gtk2
  python-httplib2 python-hyperlink python-idna python-incremental
  python-ipaddress python-jwt python-oauthlib python-openssl python-pam
  python-piston-mini-client python-pyasn1 python-serial python-twisted-bin
  python-vte python-xapian python-xdg python-zope.interface
  python3-piston-mini-client python3-xapian software-center-aptdaemon-plugins
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libcanberra-gtk-module libcanberra-gtk0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.9 kB of archives.
After this operation, 84.0 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 libcanberra-gtk0 amd64 0.30-5ubuntu1 [7,864 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 libcanberra-gtk-module amd64 0.30-5ubuntu1 [10.0 kB]
Fetched 17.9 kB in 1s (26.1 kB/s)                 
Selecting previously unselected package libcanberra-gtk0:amd64.
(Reading database ... 203248 files and directories currently installed.)
Preparing to unpack .../libcanberra-gtk0_0.30-5ubuntu1_amd64.deb ...
Unpacking libcanberra-gtk0:amd64 (0.30-5ubuntu1) ...
Selecting previously unselected package libcanberra-gtk-module:amd64.
Preparing to unpack .../libcanberra-gtk-module_0.30-5ubuntu1_amd64.deb ...
Unpacking libcanberra-gtk-module:amd64 (0.30-5ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up libcanberra-gtk0:amd64 (0.30-5ubuntu1) ...
Setting up libcanberra-gtk-module:amd64 (0.30-5ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ... 
When I tried running Xsane as root I received the message "Failed to load module "canberra-gtk-module"" So I tried loading the module as you might see above still no change. Any help might be appreciated.
```
wget
https://download2.ebz.epson.net/imagescanv3/ubuntu/lts1/deb/x64/imagescan-bundle-ubuntu-18.04-1.3.44.x64.deb.tar.gz && tar xzvf imagescan-bundle-ubunt* && sudo sh ./imagescan-bundle-ubuntu-18.04-1.3.44.x64.deb/install.sh
```

---

### Post by Joe_Linux on 2019-04-06
Not Found

The requested URL /imagescanv3/ubuntu/lts1/deb/x64/imagescan-bundle-ubuntu-18.04-1.3.44.x64.deb.tar.gz && tar xzvf imagescan-bundle-ubunt* && sudo sh ./imagescan-bundle-ubuntu-18.04-1.3.44.x64.deb/install.sh was not found on this server


I tried the link. My results are above. Thank you any way.

---

### Post by brian_p on 2019-04-07
Nlona's single command is actually three commands strung together. So, a bit of initiative; test the first one:

```
wget https://download2.ebz.epson.net/imagescanv3/ubuntu/lts1/deb/x64/imagescan-bundle-ubuntu-18.04-1.3.44.x64.deb.tar.gz
```

It works for me.

---

