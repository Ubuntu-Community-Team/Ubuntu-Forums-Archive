---
title: "ndiswrapper with wireless card broken after reboot"
date: 2010-01-01
forum: Hardware
---

### Post by mrmooge88 on 2010-01-01
I wubi installed Xubuntu 9.10 on an old Sony Vaio. Everything works except wireless. It has an expansion card for wireless G networks. (D-link dwl-630) I installed a driver for it using ndiswrapper. It worked great. Once I rebooted it stopped working. I restarted again and it did work. Today it doesn't feel like working at all.
To set up ndiswrapper I ran the commands:

cd <driver dir.
sudo ndiswrapper -i <driver>.INF
sudo ndiswrapper -l (it listed the driver)
sudo modprobe ndiswrapper
sudo iwconfig (the wireless interface showed up)
sudo ndiswrapper -m

I then added "ndiswrapper" without quotes to the end of /etc/modules
I am running version 1.55
Thanks for the help.

---

