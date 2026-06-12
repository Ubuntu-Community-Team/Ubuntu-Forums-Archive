---
title: "Battery monitor not working"
date: 2010-04-30
forum: Hardware
---

### Post by Stex on 2010-04-30
The battery monitor on the top bar is constantly missing, and when set to always display always says the AC adapter is present.

However, running acpi on the terminal gives:
Battery 0: Discharging, 72%, rate information unavailable

I've just updated to 10.04, but also had this problem intermittently with 9.10.

Is this a known issue? Any ideas?
Thanks

---

### Post by dino99 on 2010-04-30
not heard about that yet but try:

sudo apt-get install -f

sudo dpkg --configure -a

into synaptic you can search "battery": there are several packages that may be usefull, need to try

---

