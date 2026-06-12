---
title: "Aspire one zg5, how to get wifi working (Atheros AR5007EG/AR242x)"
date: 2009-09-09
forum: Hardware
---

### Post by davidkarn on 2009-09-09
So I had been struggling to get the wifi card on my aspire one zg5 working with netbook remix 9.04 for a while, doing a lot of googling and forum-reading, and gave up on ubuntu a couple times. I have it working now, this is what I did.

Wifi on the AA1 ZG5 (ar242x):

UNR defaults to the ath5k driver for me, this works initially, but the network connection eventually will randomly stop and not start again. The madwifi-hal drivers work fine, so to install, grab the most recent snapshot from [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

```

tar xfz madwifi*.tar.gz
cd madwifi*
make
sudo make install

```At this point ubuntu is still set to use the ath5k drivers. Run jocky-gtk (Administration->Hardware Drivers) and activate madwifi. If you open up /etc/modprobe.d/blacklist-ath_pci.conf, it should end with "blacklist ath5k" now, and the "blacklist ath_pci" line will have been deleted.

This is the part where I kept getting stuck at. If you reboot now ubuntu will be using the madwifi-hal drivers, but running "iwlist scan" just returns: "ath0: No scan results". To fix, ensure that the ath_pci module is loaded with the option rfkill=0. When you load the module using modprobe, use "sudo modprobe ath_pci rfkill=0", and to have the module always loaded with that option on start, create the file /etc/modules.d/options.conf and add the line "options ath_pci rfkill=0".


I'm posting that here because I think the information should be available somewhere easy to find so next time when I forget how to get madwifi working, I can find it, and the next person with the problem can too. If this forums isn't the greatest place for that, where should this info go?

---

