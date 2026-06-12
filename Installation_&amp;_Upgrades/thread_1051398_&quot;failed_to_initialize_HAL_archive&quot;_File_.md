---
title: "&quot;failed to initialize HAL archive&quot; File System/Internet gone?"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by DiscoStu9 on 2009-01-26
I upgraded to the hardy ubuntu a few weeks ago, everything has been fine, I was toying with a few packages I found to get my wireless working (intel wifi 5100), nothing seemed to work,but regardless...turned my laptop on today, and boom...

"Failed to initialize hal, archive" error on startup, and from there I cannot view my USB stick, and it no longer finds my Ethernet. These are the 2 things I need to pull some files so I can do my work. HEEELP



HP DV5T
P8600 2.4ghz
3gb RAM
64-bit VISTA / UBUNTU hardy

---

### Post by Yellow Pasque on 2009-01-26
Most of the time, the "Failed to initilaize HAL" issue can be traced to the startup priority of dbus, HAL, and gdm.
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)

---

