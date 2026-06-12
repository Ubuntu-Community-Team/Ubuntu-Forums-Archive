---
title: "HP Mini 311 Networking Help"
date: 2010-05-29
forum: Hardware
---

### Post by GrantT on 2010-05-29
Hi all...
 
Just did a clean install on 10.04 on an HP Mini 311 with the Nvidia Ion LE chipset. Everything seems to work great, but I have no networking....wired or wireless.
 
Attempted to install the Broadcom wireles drivers...but I am at a dead end...don't use Linux too much so not sure what to do.
 
Can't get past the instructions I found here.....
 
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
 
I downloaded broadcom-wl-4.150.10.5.tar.bz2 on another computer and copied the file over to the desktop via a pen-drive, which I hope are the correct drivers...but don't know where to go from here...
 
Any suggestions appreciated...the problems seem to be b43-fwcutter command...can't run them or find the packages.
 
Grant

---

### Post by jynyl on 2010-05-29
Did you look under System > Hardware drivers? (or similar menu item under Ubuntu)  The final version of Lucid has restricted drivers for many devices (not sure about the 311, though).

---

### Post by GrantT on 2010-05-29
Yes, I had looked in there.  Nothing shown.
 
Grant

---

### Post by animool on 2010-06-13
I have exactly the same problem - I tried installing and running fwcutter from the linked instructions and have had no luck either. Help - anyone??

I have had networking (wired and wireless) working OK on this netbook under Ubuntu 9.10 - I'm not sure what they've changed in 10.04 for it not to work on either.

---

### Post by garvinrick4 on 2010-06-13
And you are using network-manager package.

rick@rick-laptop:~$ aptitude show network-manager
Package: network-manager
State: installed
Automatically installed: no
Version: 0.8-0ubuntu3
Priority: optional
Section: net
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 2,417k
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libglib2.0-0 (>= 2.23.5), libgudev-1.0-0 (>= 147), libnl1 (>= 1.1),
         libnm-glib2 (>= 0.8~a~git.20090826t185111.79489be), libnm-util1 (>=
         0.8~a~git.20090930t162132.866d48b), libnspr4-0d (>= 4.7.0~1.9b1),
         libnss3-1d (>= 3.12.2~rc1), libpolkit-gobject-1-0 (>= 0.94), libudev0
         (>= 147), libuuid1 (>= 2.16), upstart-job, iproute, iputils-arping,
         lsb-base (>= 3.2-14), wpasupplicant (>= 0.6.1~), dbus (>= 0.60),
         update-notifier-common, ppp
Recommends: network-manager-gnome | network-manager-kde |
            plasma-widget-networkmanagement, dnsmasq-base, modemmanager,
            iptables, network-manager-pptp
Conflicts: network-manager-pptp (< 0.7~~)
Replaces: network-manager-pptp (< 0.7~~)
Description: network management framework daemon
 NetworkManager attempts to keep an active network connection available at all
 times. It is intended only for the desktop use-case, and is not intended for
 usage on servers. The point of NetworkManager is to make networking
 configuration and setup as painless and automatic as possible.  If using DHCP,
 NetworkManager is _intended_ to replace default routes, obtain IP addresses
 from a DHCP server, and change nameservers whenever it sees fit. 
 
 This package provides the userspace daemons. 
 
 Homepage: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

rick@rick-laptop:~$

---

### Post by fetuspuppet on 2010-06-30
I just did a basic install through wubi of 10.04 Desktop. network-manager was installed by default.

I Then plugged in my 311 to the network through the physical ethernet port, and got an automatic IP via dhcp on my lan.

I found that when you goto

System -> Administration -> Hardware Drivers

[B]And install IN THIS ORDER:

[/B]b43 Driver (The fwcutter Driver **above** the Broadcom STA proprietary driver first!!!)
Then install the Broadcom STA proprietary driver
Then install the NVIDIA accelerated graphics driver (version current)

After installing these reboot your 311.

The network-manager in the top right corner should now say "Wireless Networks Available" and if you click it it should be functional.

However - if you don't install in this order the network-manager won't work - looks like there's some scripting issues, this was the same problem on my Dell Vostro 1500.

When I now look at the System -> Administration -> Hardware Drivers the only items that are shown are the

NVIDIA accelerated graphics driver (version 173) **NOT INSTALLED**
Broadcom STA propietary wireless driver INSTALLED
NVIDIA accelerated graphics driver (version current) [Recommended] INSTALLED

So the option to install or remove the fwcutter and included drivers are now missing and this is why I was unable to find the EXACT name of the driver that is above the STA driver in the list. (again, same issue on the Vostro 1500)

Hope that helps.

---

