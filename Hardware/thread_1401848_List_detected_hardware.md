---
title: "List detected hardware"
date: 2010-02-08
forum: Hardware
---

### Post by Hawk666 on 2010-02-08
I am working on getting an xbox IR receiver working on my PC, and was wondering if there is anyway to list detected hardware (IE. list what is plugged into USB ports) the closest i have found is "lshw" but that doesn't do what i need

---

### Post by pi/roman on 2010-02-08
This one may need to be installed:
sudo apt-get install hwinfo
hwinfo --usb

---

### Post by Hawk666 on 2010-02-09
beautiful, installed and ran hwinfo and i show "Microsoft Xbox DVD Playback Kit" listed. one step closer to gettin this thing workin.

thanks very much

---

