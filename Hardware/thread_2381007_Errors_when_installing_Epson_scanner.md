---
title: "Errors when installing Epson scanner"
date: 2017-12-22
forum: Hardware
---

### Post by phdsuppo on 2017-12-22
Running 16.04 on an Intel I5 7th gen chip. After finally getting the system to install the Epson WF-3520 scanner package (after 10 tries) I got the following errors:

```
Unpacking iscan-network-nt:i386 (1.1.1-1) ...
dpkg: dependency problems prevent configuration of iscan:i386:
 iscan:i386 depends on iscan-data.
 iscan:i386 depends on libglib2.0-0 (>= 2.12.0).
 iscan:i386 depends on libgtk2.0-0 (>= 2.12.0).
 iscan:i386 depends on libltdl7 (>= 2.2.6b).
 iscan:i386 depends on libsane (>= 1.0.11-3).
 iscan:i386 depends on libstdc++6 (>= 4.4.0).
 iscan:i386 depends on libusb-1.0-0 (>= 2:1.0.6).
 iscan:i386 depends on libxml2 (>= 2.7.4).

dpkg: error processing package iscan:i386 (--install):
 dependency problems - leaving unconfigured
Setting up iscan-data (1.39.0-1) ...
dpkg: dependency problems prevent configuration of iscan-network-nt:i386:
 iscan-network-nt:i386 depends on libstdc++6 (>= 4.1.1-12).
 iscan-network-nt:i386 depends on iscan (>= 2.29.3); however:
  Package iscan:i386 is not configured yet.

dpkg: error processing package iscan-network-nt:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for udev (229-4ubuntu21) ...
Errors were encountered while processing:
 iscan:i386
 iscan-network-nt:i386
```

After much additional research I still can't find what I'm looking for. As I am a novice to Ubuntu/Linux and not a programmer, how do I resolve these errors?
any assistance really appreciated.

---

### Post by slickymaster on 2017-12-25
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by pdc on 2017-12-25
so you would have gone here [http://support.epson.net/linux/en/iscan_c.php?version=1.0.4](http://support.epson.net/linux/en/iscan_c.php?version=1.0.4) and clicked to download [COLOR="#0000FF"]iscan-bundle-1.0.4.x86.deb.tar.gz[/COLOR] and saved it to your Downloads folder; 

so from a terminal the commands would be

```
cd Downloads
```
```
tar -zxvf iscan-bundle-1.0.4.x86.deb.tar.gz
```

then as the package has an [COLOR="#FF0000"]install script[/COLOR] inside, (I downloaded the package to see what was in it ...) ....... best to run that so next command is 
```
cd iscan-bundle-1.0.4.x86.deb
``` and then 
```
sudo ./install.sh
``` and that should do things for you; 

If you tell us if that is what you did; seems to me reasonable you copy the above commands; paste them into a terminal; and attempt to get that install script to run .... if you did download [COLOR="#0000FF"]iscan-bundle-1.0.4.x86.deb.tar.gz[/COLOR]

---

