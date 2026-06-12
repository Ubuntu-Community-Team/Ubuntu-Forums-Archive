---
title: "Bluetooth Suddenly Stopped Working"
date: 2011-05-20
forum: Hardware
---

### Post by Cerin on 2011-05-20
I'm running Ubuntu 10.04 on a Macbook Pro 5.5, and I had been using Bluetooth without any problems, until yesterday when it suddenly stopped working.

I was using a Bluetooth headset, and it suddenly lost connection, the Bluetooth icon disappeared from my Gnome indicator-applet, and System->Preferences->Bluetooth dialog says I no longer have any Bluetooth adapters available.

Did my Bluetooth hardware somehow get fried, or is there any software fix I could try?

I tried restarting the bluetooth daemon via `sudo /etc/init.d/bluetooth restart`, but this does nothing, and `sudo /etc/init.d/bluetooth status` reports the daemon is still not running.

Are there any diagnostics I could run to determine what the problem is?

---

