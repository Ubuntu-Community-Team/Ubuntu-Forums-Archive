---
title: "graphics card driver installation"
date: 2010-04-19
forum: Hardware
---

### Post by daboringguy on 2010-04-19
complete nub at linux. after 5 hours of searching through forums all i found was stuff that doesnt make sense.
ive got a ati radeon xpress 1250 graphics card. ive tried installing the driver provided by ati at their website but it fails if i try to run it. im trying to play heroes of newerth.

---

### Post by Yellow Pasque on 2010-04-19
Recent proprietary ATI drivers don't support your card and the older ones that do support it don't run on newer distros (anything with X server 1.6 or later). You'll have to use an older distro like Ubuntu Hardy or Debian Lenny.

BTW, you probably fubar'd your current system by trying to install Catalyst/fglrx. See this to fix it: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

