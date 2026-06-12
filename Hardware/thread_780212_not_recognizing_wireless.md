---
title: "not recognizing wireless"
date: 2008-05-03
forum: Hardware
---

### Post by ajmohr on 2008-05-03
I have a HP dv9320us, and installed ubuntu 8.04, and it will not recognize any wireless signals or connections.  any help would be appreciated. thanks.

---

### Post by cmnorton on 2008-05-03
Is Network Manager Running?

Are you using static or DHCP addresses? 

What does your /etc/network/interfaces file look like?

Does this laptop come with a wireless off/on switch? I am asking this question, because I never expected it on my Thinkpad T61p, and it had accidentally been moved to off.

---

### Post by lswest on 2008-05-03
also, can you post the output of ```
lspci
lshw -C network
``` (paste those commands into the terminal, which can be found under applications-->accessories-->terminal)

---

### Post by ajmohr on 2008-05-03
*-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:32:54:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

it does have a switch, and i've checked that.  our wireless router is a linksys wireless g in case that helps.

---

### Post by lswest on 2008-05-03
i have the same card as you do, and i found the b43 drivers no longer support the rev 2 (check by running "lspci" in the terminal, it should say (rev 1) or (rev 2) after the listing of your card).  if it's a rev 1 do this: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

if it's a rev 2 do this
```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
download the drivers i have attached, extract them to a folder then do this:
```
cd /path/to/drivers
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
``` and it should work.  To get it working at every boot download the attached script and do ```
sudo cp /path to script/Wireless.sh /etc/init.d/Wireless.sh
sudo chmod 755 /etc/init.d/Wireless.sh
update-rc.d Wireless.sh defaults
```

**Remember: change "/path to script/" to where you have the items saved**
***Installing via apt-get requires an internet connection, such as ethernet***
****each line is one command, so copy and paste it so 1 line is one command****

---

### Post by ajmohr on 2008-05-03
alright, thanks, ill give that a try later on today, i've got some other stuff to get to at the moment.

---

### Post by UncommonGuy on 2008-05-12
Thank you very kindly, lswest. Your steps were perfect, and you went the extra step of providing the exact files needed - my Broadcom wifi now works beautifully.

Are you really in Munich too? I'll buy you a beer anytime you want.

---

### Post by knytphal on 2009-06-26
An old thread, I know, but I just wanted to thank lswest for his above post which helped me immensely to get my Broadcom wireless working on my laptop...which also happened to be a rev02.

---

### Post by strongc4u on 2009-10-22
I am totally new and my f700 does not conect via Broadcom. I do c where you say to type the commands but where is that ? I pulled up cmd and tried and that didnt work, what can i o from the begining assuming that I don't know anything at all

---

