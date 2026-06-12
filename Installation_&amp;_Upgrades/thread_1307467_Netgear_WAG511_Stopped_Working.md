---
title: "Netgear WAG511 Stopped Working"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by tuaris on 2009-10-31
After doing the upgrade to 9.10 32-bit, my Netgear WAG511 is no longer available in the network drop down menu.

---

### Post by sisterzofmercy on 2009-10-31
I had been running 9.04 on a Dell D630 with a Netgear WPN511 PCMCIA card since April/May with no problems at all.

Yesterday I clean installed 9.10 and the network stopped working i.e. there were no interfaces in the list and the 'enable wireless' box was greyed out. After a bit of time looking into both the ath5k driver and some crda issues I installed Wicd. Everything then starting working and I could successfully connect to my WAN (although I still don't have access to channels 12 & 13, but that's a different story).

---

### Post by tuaris on 2009-11-02
I was hopping to fix this without installing Wicd, but if it's the only way to get my WAG511 working again, then I guess I have no choice.

IFCONFIG doesn't list my card.  Will Wicd still work for me?

---

### Post by tuaris on 2009-11-12
I was able to fix this.

Open up a terminal and type in:

```
sudo gedit
```

Open the file /etc/modprobe.d/blacklist-ath_pci.conf

Change: 
blacklist ath5k

To:
#blacklist ath5k

Save

Then open the file /etc/modprobe.d/madwifi.conf

Change: 
blacklist ath5k

To:
#blacklist ath5k

Save
Close
and Reboot

Your wireless will now work.

---

