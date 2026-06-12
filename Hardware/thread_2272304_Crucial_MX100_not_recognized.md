---
title: "Crucial MX100 not recognized"
date: 2015-04-05
forum: Hardware
---

### Post by ubuntubrian on 2015-04-05
I purchased a Crucial MX100 SSD and connected it to my laptop (in an enclosure) via USB. The MX100 is not recognized and does not mount nor show up in any disk utility. I have read that this could be a Bios issue but I'm reluctant to start messing around without clearer and more recent info. Has anyone had this experience and how was it resolved? My laptop is an Acer amd I'm running 14.10.

Many thanks

---

### Post by weatherman2 on 2015-04-05
Have you used this enclosure with other drives successfully?  Or is the enclosure new, too?

A new drive must be initialized before it can be partitioned.  And it can't be used for anything (won't show up to be mounted) until you create at least one partition.  I usually use Gparted to create the initial partition table then the partition(s).  (You may have to install Gparted.)

If you can't see the drive even with Gparted, type these terminal commands and show the output here:

```
lsusb
```

```
dmesg | grep -i usb | tail -100
```

---

### Post by ubuntubrian on 2015-04-05
After rebooting to check my Bios settings, which I didn't need to change, the drive shows up in Gparted. I don't have a clue why it did so but that's OK. Now I'll clone the drive and go SSD.
Thanks Weatherman2

---

### Post by MartyBuntu on 2015-04-06
The drive is in an external USB 3.0 enclosure, attached to a USB 3.0 port on the laptop?

---

