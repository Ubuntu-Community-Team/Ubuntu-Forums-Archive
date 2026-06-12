---
title: "Acer Aspire 5520g with Atheros AR5007EG success."
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by growler on 2008-04-01
These instructions were found after many hours searching forums from the major distros and came from Andrew Straw (sorry I can't find the link!).

Acer Aspire 5520g with Atheros AR5007EG 

Installed ubuntu-8.04-beta-desktop-i386.iso  and updated.

Sound worked from the beginning

dl@Turion:~$ uname -a
Linux Turion 2.6.24-12-generic #1 SMP Wed Mar 12 23:01:54 UTC 2008 i686 GNU/Linux



{{{

sudo apt-get install build-essential

#remove all linux-restricted-modules-*packages

sudo rmmod ath_pci
sudo rmmod ath_hal
sudo rmmod wlan

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xvzf madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make
sudo make install

# reboot without ethernet connected

}}}

No setting of Keyring password was required, just selected my  ESSID and set WPA2PSK pass phrase and it connected.

growler :KS :KS :KS

---

