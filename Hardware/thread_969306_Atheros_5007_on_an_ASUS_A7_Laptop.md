---
title: "Atheros 5007 on an ASUS A7 Laptop"
date: 2008-11-03
forum: Hardware
---

### Post by toddedw on 2008-11-03
My ASUS A7 has an Atheros 5007EG wireless card installed. LSPCI shows the following:
[INDENT]07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
[/INDENT]

I tried many methods to get this card working properly. Anything using ath_hal or ath_pci is unstable (in my case). I recommend using ath5k. I can even do packet injection with aireplay-ng now at a rate of 500 PPS. In order to use the ath5k module just follow these instructions:

Go to a terminal and type:
sudo apt-get install linux-backports-modules-intrepid-generic

After that installs click on System -> Administration -> Hardware Drivers

Make sure that:
1.) Support for Atheros 802.11 wireless LAN cards is Disabled.
2.) Support for 5xxx series of Atheros 802.11 wireless LAN cards is Enabled.

At this point your wireless card should be working, but we're not done. If you rebooted right now your wireless card would stop working. That's because madwifi blacklists the ath5k module.

Now go back to terminal and type:
sudo gedit /etc/modprobe.d/madwifi

Somewhere in that file you should find the following two lines:
[INDENT]## ath5k (mac80211)
blacklist ath5k[/INDENT]

Place a # in front of *blacklist ath5k* in order to comment it out so that the ath5k module will load at boot time.

Now you're done. Now you're free to play with aircrack-ng. Just type airmon-ng start wlan0 and that should create a mon0 device for your monitoring and injecting pleasure. Enjoy.

---

