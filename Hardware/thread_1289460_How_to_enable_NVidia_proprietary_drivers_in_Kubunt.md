---
title: "How to enable NVidia proprietary drivers in Kubuntu?"
date: 2009-10-12
forum: Hardware
---

### Post by MountainX on 2009-10-12
Just installed Kubuntu for the first time. Installed on my ThinkPad T61p. Can't find out how to install the restricted drivers.

Also, does anyone know how to get the Trackpoint (mouse pointer) working well? I want it to move much faster with lighter pressure.

Thanks

---

### Post by dabl on 2009-10-12
Kmenu > Applications > System > Hardware Drivers. Be very patient -- the driver downloads in the background and does not give visual feedback while that is happening.

---

### Post by MountainX on 2009-10-12
> **dabl said:**
> Kmenu > System > Hardware Drivers. Be very patient -- the driver downloads in the background and does not give visual feedback while that is happening.

Thanks. I forgot to mention I using Karmic. Something must be different... I finally stumbled onto it under Kmenu > Applications > System > Hardware Drivers

Not sure why it is under Applications...

---

### Post by dabl on 2009-10-12
Oooops -- yep, I forgot the "Applications" thing -- I'll fix my post above.

If it happens that Hardware Drivers fails to install the Nvidia driver, then your "Plan B" is to download it and install it manually.  It's not as convenient, but works just as well.

A slightly antiquated "how to" for that is here:  [http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892](http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892)

Note that for 9.10 and later, the command to stop KDM is ```
sudo service kdm stop
``` vs. the previous ```
sudo /etc/init.d/kdm stop
```

---

### Post by MountainX on 2009-10-13
I switched to OpenSUSE KDE 11.2 milestone 8

---

### Post by dabl on 2009-10-13
OK .... I guess you'll be getting the rest of your help on the SUSE forums.  :popcorn:

---

### Post by MountainX on 2009-10-13
Well I am still running Ubuntu on my desktop. But for KDE, OpenSUSE is shockingly ahead of Kubuntu. I mention it here in the hope that Canonical will put more resources into KDE. I'm not ready to jump ship entirely (yet). But trying OpenSUSE was an eye opening experience, I gotta say.

---

