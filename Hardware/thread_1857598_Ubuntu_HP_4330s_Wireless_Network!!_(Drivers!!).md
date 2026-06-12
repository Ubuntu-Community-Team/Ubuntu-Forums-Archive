---
title: "Ubuntu HP 4330s Wireless Network!! (Drivers!?!?)"
date: 2011-10-10
forum: Hardware
---

### Post by skillew on 2011-10-10
Hi :) 

I recently installed ubuntu on my HP 4330s laptop. Well everything works fine, except for the wireless network. I can't seem to get it to work. Plus the button you could press to turn wireless networking on and off in Windows have changed to a switch for bluetooth. I've look for network drivers, but I can only find it for other linux. I dunno if the driver is causing those problems, but It's worth a try. 

The driver I'm looking for is RaLink RT3592. 

Btw, connecting to internet trough a cable works.

---

### Post by skillew on 2011-10-11
Bump

no fix??

---

### Post by Scabby_al on 2011-10-11
I have an HP Probook 4420s with the RT3090 card and while the drivers worked, I had issues with reception and card speed. I had to do the following to get my card to work properly

> sudo modprobe -rf rt2800pci
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta

Network manager should start trying to connect or find a wireless network.
Test at this point to see if there is any connectivity.

To make the changes permanent:

echo blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf

With Ubuntu 11.10 and the latest updates with Fedora 15, I don't need to do this at all. (must have been the kernel updates)

Not sure if this will work since we don't have the exact same card but it might be worth a shot if you're having a lot of issues. If not, perhaps give 11.10 a shot?

---

