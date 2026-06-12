---
title: "Linksys WUSB600N"
date: 2009-12-26
forum: Hardware
---

### Post by mcgodx on 2009-12-26
Hey all, I bought my mom an old Compaq Presario 2500 laptop for $60 when her old one broke (she doesn't need speed at all), and the problem is, it has no built in wireless.

I have a Linksys WUSB600N (wireless N USB adapter based on a Ralink chipset).  I plugged it in to the laptop, and Network-Manager detects it, and it will connect (intermittently) to the network, however no traffic seems to make it (and when I go to view the connection information, it says it's at 1MB/s or "unknown").

If anyone has been able to get this to work, I'd appreciate any help!  I bought another Linksys adapter but it seems to be having a worse issue, I'll probably be returning it though.  This is a WUSB54GC, another Linksys card.  This card won't even connect to the network.

Thanks again.

---

### Post by Old_Grey_Wolf on 2009-12-26
Using the Driver CD that came with the device.

Make sure that you have the "Windows Wireless Drivers" application installed on your system.

If not, you can install via menu bar...
Click Applications - Add/Remove.
On the search bar, type "Windows Wireless" (without the quotes).
Select it then "Apply Changes"

- With that one sorted out...
Go to System - Administration - Windows Wireless Drivers.
Enter your root password.
Click "Install New Driver"
Browse for the .inf file on the Driver CD that came with your device.
Click "Install" then "Close"

- You should now be able to see a wireless device on the network icon at the right side of your Applications Menu.

- Configure your wireless device and that's it!!!

NOTE: If by chance the wireless is not listed on your networks, try restarting your machine.

---

