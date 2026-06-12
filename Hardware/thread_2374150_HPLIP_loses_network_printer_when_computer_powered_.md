---
title: "HPLIP loses network printer when computer powered down"
date: 2017-10-13
forum: Hardware
---

### Post by grege2 on 2017-10-13
I have an HP CP1025nw connected via ethernet and I am running zesty beta. I can install my printer and it works fine. Except when I turn the computer off the printer is gone when I next log in. The config is still there, as when I reinstall each time it does not ask me to download the firmware. It recognises that the firmware is still there. On my note book running 16.04 the printer is there and always installed as it should be. It is a bug of some sort. Anyone else having this issue with networked HP printers?

---

### Post by ajgreeny on 2017-10-13
Can you confirm that the printer is connected by ethernet cable and we are not dealing with a wireless connection.

If using wireless the printer really needs a static local IP or it is possible for the IP to change depending on what else is connected to the router but if using a cable I would not anticipate this being a problem.

---

### Post by grege2 on 2017-10-13
Definitely ethernet and the IP address has not changed.

---

### Post by kurt18947 on 2017-10-14
I'm not an HP user but had problems in the past with printers not being found after a restart. I started assigning static I.P. addresses to networked printers and using an HP protocol. I assign a printer I.P. address outside the range used by DHCP. My URI address to a printer would look something like ```
socket://xxx.xxx.xxx.xxx:9100
``` I haven't 'lost' a printer since.:)

Edit: I recently installed 17.10 to see how Ubuntu has implemented the Gnome desktop. Much to my surprise and delight 2 networked printers (Brother & Samsung) were found and installed. There was no need to install any drivers. I did check that both printed though I didn't check any advanced features like duplexing.

---

### Post by grege2 on 2017-10-16
Thanks, I will try a static address at some point. I suppose I should also just uninstall everything and re install. I will sit until Zesty is live and see what happens.

---

### Post by grege2 on 2017-10-17
As a workaround I removed HPLIP and used the add printers app in settings and it found the printer. Now it survives reboots but there is no monitoring of ink levels. Never mind it works. It is also missing from CUPS when you go to localhost:631. Yet it works and the firmware downloaded by HPLIP is there some where to be used. In the long run I will manually download HPLIP from HP once they update it for Zesty. This printer and driver have been flawless for many years so this bug is a pain.

---

### Post by grege2 on 2017-10-23
[SOLVED] Once the final release or artful arrived I uninstalled then reinstalled and since then HPLIP has worked properly and it maintains the setup between reboots.

---

