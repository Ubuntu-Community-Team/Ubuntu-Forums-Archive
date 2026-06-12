---
title: "Live usb creator missing"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by eppoh on 2008-12-27
How can I get live usb creator? I have done a search in synaptic for the package, but nothing comes up.

I am running 8.04 with Kubuntu.

---

### Post by logos34 on 2008-12-27
> $ apt-cache show **usb-creator**
Package: usb-creator
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 200
Maintainer: Evan Dandrea <evand@ubuntu.com>
Architecture: all
Version: 0.1.10
Depends: python, python-central (>= 0.6.7), gksu, python-gtk2, python-glade2, python-dbus, syslinux, parted
Description: Ubuntu USB desktop image creator
 This is a simple utility designed to make bootable USB desktop images from
 Ubuntu CDs.
Python-Version: current


$ apt-cache show **liveusb**
Package: liveusb
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 188
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Version: 0.1.1
Depends: gksu | kdesu, python, python-glade2, python-support (>= 0.7.1), python2.5-gtk2, syslinux (>= 2:3.35), ubiquity, util-linux (>= 2.10)
Description: Create a bootable Ubuntu Live USB stick from a running Live CD
 This is a tool to create a bootable Live USB stick
 from the running Ubuntu Live CD.
 .
 It was made in response to Ubuntu Brainstorm idea #16.
Homepage: [http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/)
Original-Maintainer: probono <probono@myrealbox.com>
Python-Version: 2.4, 2.3, 2.5



[https://launchpad.net/~probono/+archive](https://launchpad.net/~probono/+archive)
[https://launchpad.net/ubuntu/intrepid/+source/usb-creator](https://launchpad.net/ubuntu/intrepid/+source/usb-creator)
[http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/)

---

### Post by caen1944 on 2008-12-30
usb-creator is not part of the 8.04 distribution. I haven't yet figured out how to install it on 8.04 but supposedly it is easy to do.

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

I just started to try to do this. I'll reply again when I figure it out.

By the way, on my eee-pc laptop running 8.10, the usb-creator app work spectacularly.

---

### Post by logos34 on 2008-12-31
> **caen1944 said:**
> usb-creator is not part of the 8.04 distribution. I haven't yet figured out how to install it on 8.04 but supposedly it is easy to do.

yes.

[http://ubuntuliving.blogspot.com/2008/11/usb-creator-for-hardy.html](http://ubuntuliving.blogspot.com/2008/11/usb-creator-for-hardy.html)

I have the x64 version 'usb-creator_0.1.10_all.deb' installed on 8.04 ubuntustudio.

---

