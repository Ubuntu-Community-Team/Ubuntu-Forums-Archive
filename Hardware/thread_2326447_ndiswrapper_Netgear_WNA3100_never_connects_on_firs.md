---
title: "ndiswrapper Netgear WNA3100 never connects on first Boot at Morning"
date: 2016-06-01
forum: Hardware
---

### Post by steffomix on 2016-06-01
Ubuntu 16.04 on x64.

After install a Netgear WNA3100 every morning the WLan Stick does not connect to local Network properly.

It took a while of uninstall-install sequences until I recognized that the Stick has problems only on first Boot at morning. 
To fix that simply reboot the Machine. A replug will not help. 

The only thing I detected that may cause the problem is that tx-power is on first boot at 32dbm what is way to high. After reboot tx-power is at 24dbm. Power Management is set to off.

On Windows I have the opposite Problem:
Booting the Machine with plugged in WLan Stick will cause in not connecting to local Network but a simple replug fix it.

However, I can live with this Bug. But it took a while and many attempts to throw the Stick to trash before I detected to simply reboot the Machine and all is fine...

---

### Post by X-RED_Tech on 2016-06-02
Perhaps you should have trashed it.
There are many which have native support.

---

