---
title: "Installing another hard drive"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by simplified on 2009-03-30
Hi All

I was hoping that someone could help me with installing a new SATA drive into my Ubuntu 8.10 box. What I'd ideally like to achieve is to install the new drive, format it as ext3 and then merge it together with my existing hard drive as an LVM partition.

Not really sure where to start... I was going to install the drive and format it with the command:

```
# mkfs.ext3 /dev/**[COLOR="Red"]harddrive[/COLOR]**
```

.. and then go into the LVM applet and join both my existing HDD and the newly installed and formatted drive into the LVM group. I don't know if anyone has done this as it's obviously a bit dodgy if you don't know exactly what you're doing and I don't really want to have to install again from scratch...

Any opinions, suggestions or comments would be most appreciated.

Thanks, OL

---

