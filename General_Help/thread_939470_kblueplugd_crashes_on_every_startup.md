---
title: "kblueplugd crashes on every startup"
date: 2008-10-05
forum: General Help
---

### Post by ger_macaco on 2008-10-05
Hi, I have upgraded to Kubuntu Intrepid Ibex and I'm running it on an amd64 PC.

kblueplugd keeps crashing on every startup. My USB Bluetooth dongle is plugged in.

"Bluez DBus interface not available"

Any help on this?
Many thanks!

---

### Post by carolinason on 2008-10-09
same here on plain old 32bit with no bluetooth devices

---

### Post by Yellow Pasque on 2008-10-09
The problem has been reported. [https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/279983](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/279983)

> Yes. The problem is a new version of the bluetooth libraries was uploaded
without it being tested against KDE. We are broken until the package can
be changed to work with the newer infrastructure.

---

