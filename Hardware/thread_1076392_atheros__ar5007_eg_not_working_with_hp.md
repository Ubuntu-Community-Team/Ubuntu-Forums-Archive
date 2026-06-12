---
title: "atheros  ar5007 eg not working with hp"
date: 2009-02-21
forum: Hardware
---

### Post by cwill08f on 2009-02-21
I've tried installing madwifi and Windows wireless drivers and so far it's turned off still. I can't find the problem. Windows wireless drivers says the hardware's there but nothing I do can turn it on!

iwconfig says is disabled.

I'm really lost here.

The computer is an Hp pavillion.

---

### Post by sjoewert300 on 2009-02-21
> **cwill08f said:**
> I've tried installing madwifi and Windows wireless drivers and so far it's turned off still. I can't find the problem. Windows wireless drivers says the hardware's there but nothing I do can turn it on!

iwconfig says is disabled.

I'm really lost here.

The computer is an Hp pavillion.

Hi,
I had the same problem, but I solved it with the help of the following page:
[http://sites.google.com/site/computertip/atheros](http://sites.google.com/site/computertip/atheros)
It's a Dutch page, but I'll make a translation:


This works for Ubuntu 8.04 and 8.10

1. Make a wired connection.

2. Disable both drivers for Atheros 802.11 WLAN cards in System > Management > Hardware Drivers

3. Restart your laptop

4. Download the Madwifi driver: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz")

 This is not a fully functional driver but a package to generate a driver. That is because there are many Linux-distributions.

5. Replace the file to "home" (Locations > Personal folder)

6. Unpack the tar.gz file

7. Start your terminal and copy/paste this:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

8. Go to the folder with the Madwifi driver:
```

cd madwifi-hal-0.10.5.6-r3942-20090205
```

9. Type:
```
make
```
**!!** Wait until this operation is done! So wait until you see: yourname@pcname:~$

10. Install the driver:
```
sudo make install
```
**!!** Wait until this operation is done! So wait until you see: yourname@pcname:~$

11. Load the kernel-modules:
```
sudo modprobe ath_pci
```

12. Make sure the modules are loaded every time your computer starts:
```
gksudo gedit /etc/modules
```

13. Add this line to the file at the very bottom:
```
ath_pci
```
For example:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ath_pci
```

14. Restart your PC.


Now your Atheros device should work.. If not let me know..

GOOD LUCK :D

Cheers,
sjoewert

---

### Post by mnopneal on 2009-02-24
This procedure did get wireless working for me on an HP dv7-1245dx Pavillion running 8.04 64bit.  I did NOT manage to get wireless working with 8.10, even with the backports mess.    8.10 didn't even get the link light running on the wired port, so I gave up and install 8.04.   Thank you for the clear documentation.   Perhaps it's really important to have the ath_pci in the modules file at boot time for the other networking UI pieces to notice the connection?

---

### Post by binbash on 2009-02-25
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

