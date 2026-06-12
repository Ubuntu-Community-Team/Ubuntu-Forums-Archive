---
title: "hardy - stop loading ssb module"
date: 2008-04-27
forum: Hardware
---

### Post by rogier.de.groot on 2008-04-27
to get wireless working I use ndiswrapper. However, ndiswrapper won't work at boot because the 'ssb' module is loaded. If I do:
sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe ndiswrapper
wireless will work, but I want to stop my system from loading ssb in the first place; I tried adding 'blacklist ssb' to /etc/modprobe.d/blacklist but that doesn't seen to do the trick.

---

### Post by rogier.de.groot on 2008-04-29
Bump

---

