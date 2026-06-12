---
title: "Gnome Power Manager"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by theotherme on 2007-07-31
My gnome-power-manager tray icon stopped working. It seems to be a hal issue. lshal shows no battery after boot, however if I restart hal (/etc/dbus-1/event.d/20hal restart), it detects the battery just fine and the tray icon works again. How do I fix it so hal detects the battery at boot?

---

### Post by theotherme on 2007-07-31
bump

---

### Post by theotherme on 2007-08-01
Never mind, I fixed this by changing S99acpid to S10acpid in /etc/rc2.d

---

