---
title: "Vodafone K3565-z and flakey Wireless Broadband modem net connection"
date: 2009-12-18
forum: Hardware
---

### Post by WSDsmurf on 2009-12-18
Hi all,

Just thought I would post up my experience/problems/fix as a few people seem to have been having the same problems.

Using Ubuntu 9.10 on laptop.
With Vodafone K3565-Z (which as far as I can tell is the same as a Huawei e160) sim-card usb wireless broadband modem.  Which has onboard memory housing winXP modem drivers, manauls etc - which handily meant that the device kept showing up in Ubuntu as a connected USB storage/CD device instead of as the modem.

Was having issues with Ubuntu showing as a USB-key / CD device, and not being available for selection as connection option in Network Manager (standard version), even though had installed as such.

Was also having issues of even when device was recognised, and Network Manager was using it to connect (ie showing as connected in system tray, and device blue-LED showing successful 3g connection), that network dependant apps would still not be able to find a network connection (ie Firefox still not working).

Followed advice here
[http://ubuntuforums.org/showthread.php?t=1336197](http://ubuntuforums.org/showthread.php?t=1336197)

Installed non-supported new version of Network Manager (v0.7.997).

Now, I still get usb-storage device/cd device upon initial startup, just right click the storage device icon and 'eject'... and then the 3g device is picked up Network Manager and connects.

Firefox etc have no problem finding the connection now.

(Sometimes the Network Manager decides its been told to 'disable netorking' at startup, after eject, but a right click on the NManager icon can fix that.).

So.... in short, 9.10 with this particular popular 3 modem still isnt perfect, but is at least working smoothly (better than a poke with a stick when your travelling).

---

### Post by acesabe on 2010-01-20
Added newer network-manager packages linked to above - also resolves plack of plug-and-play function previously missing. Thanks.

Ubuntu 9.10 upgraded 20th Jan '10

---

