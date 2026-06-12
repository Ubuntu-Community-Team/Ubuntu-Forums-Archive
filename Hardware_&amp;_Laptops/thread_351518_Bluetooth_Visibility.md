---
title: "Bluetooth Visibility"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by Ehnvis on 2007-02-02
I got a HP NC4010 laptop (12" screen, really love this thing) which has built in bluetooth and wlan and both works fine. Running Ubuntu 6.10, installed the gnome-bluetooth package as bluez was already on the system.

Problem is the bluetooth, found out a few days ago (only had Ubuntu installed for a week now but has been running gentoo for 2 years) that the bluetooth is default in visibility mode and anyone that does a scan can see it.

In the /etc/bluetooth/hcid.conf there is a line which should handle the visibility mode and thats the iscan enable/disable parameter. Discovto only tells the system for how long it should be visible. Problem is that when I played around with the parameters I got the laptop to go to invisible mode and wont go back to visible mode again.

Anyone else encountered this problem and know how to fix it? To me it seems like the system doesn't even read the hcid.conf file as changes in it does nothing.

---

### Post by Ehnvis on 2007-02-02
Found out that using the command dbus-send with the right parameters will turn on the bluetooth visibility. Wierd solution in my eyes but right now it seems like I have to live with it.

Still kinda confused why changes in hcid.conf doesn't do anything.

---

### Post by adwait on 2007-02-20
I am having a similar problem, could you post the command that you used?

---

### Post by Ehnvis on 2007-02-26
Sorry for the late response but here is the command.

dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable

---

