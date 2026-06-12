---
title: "Problem Toshiba Satellite U305-S7467 Bluetooth"
date: 2008-05-08
forum: Hardware
---

### Post by Gcentenari on 2008-05-08
Hello

I have a Toshiba Satellite U305-S7467 with Ubuntu 8.04  and my Bluetooth is not working.
I try to do the forums tips but not work.

My "hcitool scan" response:
Device is not available: No such device

My "dmesg |grep Bluetooth" response:

[ 49.538840] Bluetooth: Core ver 2.11
[ 49.539156] Bluetooth: HCI device and connection manager initialized
[ 49.539162] Bluetooth: HCI socket layer initialized
[ 49.578537] Bluetooth: L2CAP ver 2.9
[ 49.578545] Bluetooth: L2CAP socket layer initialized
[ 49.660322] Bluetooth: RFCOMM socket layer initialized
[ 49.660334] Bluetooth: RFCOMM TTY layer initialized
[ 49.660336] Bluetooth: RFCOMM ver 1.8

Thanks a lot.
Sorry for my English :(

---

### Post by nozyczek on 2008-08-20
Same here.
Anyone? Please ...

---

### Post by nozyczek on 2008-08-25
This worked for me.
Credit goes to Tim Richardson
It was copied from here:
[http://iorek.rikva.nl/cms/index.php?itemid=5](http://iorek.rikva.nl/cms/index.php?itemid=5)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Tim Richardson wrote:
To follow up on getting bluetooth to work on Ubuntu Hardy, I did this:

1) visit this site, and add the Debian sid repository
[http://packages.kirya.net/](http://packages.kirya.net/)
it is not necessary to add the source repository.

1a) refresh synaptic, and add the package
omnibook-source

2) use module-assistant to build the kernel module (but first, exit synaptic)
sudo m-a a-i omnibook-source
(you have to work out how to get module-assistant working yourself. It is a package; you can find it in Synaptic. Make sure you install all recommended dependencies. Try installing build-essential as well)

3) we need to make sure the module loads at startup
so edit the file /etc/modules
sudo vo /etc/modules
and add the line
omnibook
at the end

4) and we need to get it working so make a file called omnibook in /etc/modprobe.d
and in this file put one line
omnibook ectype=14

5) you don't need to reboot. You can do this
sudo modprobe omnibook ectype=14

by doing this, the bluetooth icon appears.
08/07 13:14:05
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Good luck
nozyczek

---

