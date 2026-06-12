---
title: "Toshiba Satelite A305D ATI Radeon X1250 and Atheros AR5008X"
date: 2008-07-24
forum: Hardware
---

### Post by stevensdale on 2008-07-24
I just installed ubuntu-8.04.1-desktop-amd64 on a Toshiba Satelite A305D-S6835.
Everything went well except the Atheros AR5008X and the ATI Radeon x1250.

I would like to get the WiFi working (my only internet option in Kuwait) so I can fix the ATI using SPM.

I found this:
Build essential packages by System-Administration-Synaptic Package Manager
Insert Ubuntu CD, in SPM go to edit- Add CD-ROM
In Build-essential, Mark for Installation
Apply for marked changes

Download the driver from
[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
cd madwifi-ng-r2756+ar5007
make
sudo make install
sudo modprobe ath_pci
sudo reboot

from Toshiba web site but have NO IDEA how do make any of it work.  When I try to follow the instructions I am not doing something correct.  THe problem may be my Ubuntu CD, even though it verified 100% before the install.  When I attempt to:

In Build-essential, Mark for Installation
Apply for marked changes

I get errors about the CD being unavailable, or unable to mount.

Thank You!

---

