---
title: "Double keystroke with MCE Remote"
date: 2011-12-29
forum: Hardware
---

### Post by Superdude_123 on 2011-12-29
I keep getting two strokes for each press with my MCEUSB remote. Anyone know how to fix this?

---

### Post by Superdude_123 on 2011-12-29
Found the solution and do as follows:

Try this:

sudo sed -i '$i echo lirc > /sys/class/rc/rc0/protocols' /etc/rc.local

Read [http://ubuntuforums.org/showthread.php?p=11525835](http://ubuntuforums.org/showthread.php?p=11525835) for the exact know how and why (bottom)

---

