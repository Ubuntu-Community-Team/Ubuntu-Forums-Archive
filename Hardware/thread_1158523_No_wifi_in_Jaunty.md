---
title: "No wifi in Jaunty"
date: 2009-05-13
forum: Hardware
---

### Post by steve01832 on 2009-05-13
There seems to be a growing problem with Linksys pcmcia wifi adapters after upgrading to Jaunty. Type in  ls -la /etc/modprobe.d you will find a few files of blacklisted drivers. Linksys devices use Atheros drivers or madwifi drivers. Mostly you will want to use ath5k or ath_pci driver. These are all blacklisted by default in Jaunty. Open a terminal and type 
sudo gedit /etc/modprobe.d/madwifi.conf and comment out (#) the very beginning of the line next to the driver you want to use. Hit save and restart the computer. The new driver should be brought up. I recommend using ath_pci due to the fact that you can fine tune the card's Tx output and scan with this driver. Good luck and enjoy Jaunty. It is the nicest Ubuntu so far (strictly my opinion though).

Steve

---

