---
title: "EXT HDD.volume"
date: 2010-02-08
forum: Hardware
---

### Post by Curtiee on 2010-02-08
Is there anyway to stop the shortcuts that appear on your desktop when an external hard drive or other media device is plugged in?

Cheers,
Curt

---

### Post by Morbius1 on 2010-02-08
There is one way:

Open **Terminal**
Type **gconf-editor**

Go to apps > nautilus > desktop > volumes_visable and uncheck it.

Unfortunately this has repercussions as it pertains to all volumes:

It will also not show any internal partitions that you mount through nautilus.

You won't have any mount icons for remote shares.

And you'll have to open Nautilus to unmount the device before removing it .

---

