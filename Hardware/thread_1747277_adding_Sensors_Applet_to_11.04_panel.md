---
title: "adding Sensors Applet to 11.04 panel"
date: 2011-05-02
forum: Hardware
---

### Post by tylerd1994 on 2011-05-02
Before the 11.04 upgrade, I had a CPU temperature monitor set up on my panel. Since the upgrade I haven't been able to locate that applet, though it's still on my computer (I tried to re-install it via command line) but it said it was already there, and the instructions to add it to my panel no longer work.

---

### Post by novus721 on 2011-05-03
Possible solution here:

[http://askubuntu.com/questions/33976/is-there-a-hardware-temperature-sensor-indicator](http://askubuntu.com/questions/33976/is-there-a-hardware-temperature-sensor-indicator)

---

### Post by novus721 on 2011-05-03
And actually check to see if there is any sort of config file in the program's directory that you could edit using either nano or gedit. If so, open it and see if any obvious fields such as ```
option name="enable_application_indicator_support" value="true"
``` are marked as "false" instead. 

All credit here: [http://askubuntu.com/questions/35141/radio-tray-icon-applet-not-working-in-unity](http://askubuntu.com/questions/35141/radio-tray-icon-applet-not-working-in-unity)

---

