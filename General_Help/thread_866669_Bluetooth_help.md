---
title: "Bluetooth help"
date: 2008-07-22
forum: General Help
---

### Post by silvagroup on 2008-07-22
Bought a Belkin F8T012-1 that of course works with my XP laptop, but no such luck with my Kubuntu desktop.

When I plug it in the blue led comes on, and I can launch kbluetooth.

I then turn on my Palm Centro and I can see my desktop as a device but when I try to connect it won't.

I never get to see my Centro on Kbluetooth.

If I unplug the device it locks my system up, screen goes black and I have to do a hard reboot.

Thought it maybe Gutsy related but it doesn't works exactly the same with hardy.

Any suggestions would be greatly appreciated.

---

### Post by ajmorris on 2008-07-22
hi there,
are there any errors outputed to the CLI if you start kbluetooth from a terminal? Also, could you paste your /var/log/syslog after a freeze. (either use the [code] envelops or pastebin as this file is quite long)

AJ

---

### Post by silvagroup on 2008-07-22
Thanks for your quick reply, shortly after posting I found that the trick to getting this Belkin working is to blacklist the pegasus kernel module.
/etc/modprod.d/blaclist then add blacklist pegasus.

That came from some more searching on the web.

It appears there is a problem with some naming or something. However the solution altough far from perfect works for now.

With the BT dongle in the usb this bug will also keep your system from booting correctly, won't boot at all, unless you black list pegasus.

Now to figure out how to hotsync my Palm !!!!!

---

