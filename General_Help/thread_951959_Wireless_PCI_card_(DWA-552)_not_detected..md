---
title: "Wireless PCI card (DWA-552) not detected."
date: 2008-10-18
forum: General Help
---

### Post by Alonsus on 2008-10-18
Hello,

I've recently installed a D-Link DWA-552 wireless card, however the card is not detected, i.e. lshw does not show it.

I get the same results with both 8.10 Beta and 8.04.

When booting I see the message:
"pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]"

dmesg also shows several lines of the form:
"iomem range xxxxxxxx-yyyyyyyy could not be reserved"
all with varying memory ranges

I've seen posts elsewhere about the "can't allocate mem resource" message, but most of the posts seem to be about disabling the warning.

I've tried adding:
reserve=0xdfffffff,0x2000
pci=nommconf
to the boot line but it did not work.


I've been forum scraping for several hours and have not come across a solution...

Any ideas?

---

### Post by spiderbatdad on 2008-10-18
make sure you are updated:```
sudo apt-get update && sudo apt-get upgrade
```

Then try:
```
sudo modprobe pcmcia && sudo modprobe pcmcia_core
```
Now reboot. Try to launch your browser even if network manager shows no connection.

lol. sorry, Thought you were talking about a pcmcia card

---

