---
title: "How to install 802.11b PCMCIA card (RTL8180)"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by sesquipedality on 2005-01-17
Hi,
 
I have a wifi card which appears in the device manager as a Realtek RTL8180.  Unfortunately no drivers are loaded for it.  How do I get it to work?  I'm using the linux-686 kernel package.

Thanks.

---

### Post by sesquipedality on 2005-01-17
I also tried a Belkin FSD6020 v2, and this one doesn't even seem to be detected by pcmcia (although the light does come on on the card).

---

### Post by sesquipedality on 2005-01-17
I also have a D-link DWL-G122 USB adapter.  This, like the first one is detected by the hardware, but no wifi driver appears to be installed.

---

### Post by el toro on 2005-01-21
The Belkin Card works great--I have one.  You have to enable the universe repository and then install the package "atmel-firmware", then restart PCMCIA services before it will work though.  You also might have to manually add its device name (e.g. "eth1" on my machine) to /etc/network/interfaces, but I think if you configure it in the Networking controls for Gnome, that should add it there as well.  If you get stuck take a look at the entry for your built-in ethernet card.  Let me know if it works.

---

### Post by martyr on 2005-01-25
If your cards have prism chips, you should be fine with linux-wlan-ng. It supports PCI, USB and PCMCIA.

If they aren't or if linux-wlan-ng doesn't work for any other reason, try loading a windows driver with ndiswrapper.

---

### Post by snowblink on 2005-01-25
I have a Netgear MA521, which has a 8180L Realtek chipset. I got it working by using ndiswrapper. Here is the relevant snippet from my [blog entry](http://www.snowblink.co.uk/archives/2005/01/23/ubuntu_410_on_a_sony_vaio_fx705/):

Netgear MA521 Wirless PCMCIA card

This was the one thing I was dreading. Under SUSE 8.2 this was quite tricky to get working. Thankfully things have progressed, and there is now an easy way to get this working. We use the Windows driver. Clever eh?

Download the latest windows 2000 driver (make sure it says ndis in the filename) from Realtek. Go to their site and enter 8180L into the search box, the go to Downloads. Unzip this file somewhere friendly.
# apt-get install ndiswrapper-utils
# ndiswrapper -i NET8180.INF
# modprobe ndiswrapper

check your dmesg
# ndiswrapper -m

Configure via the network configuration tool. Done. Hurrah!

---

