---
title: "Ubuntu doesn't display Sata HD"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by kampsj on 2008-02-10
switching my HTPC from vista over to linux.

I've been able to get everything working fine but I have a 250gb IDE HDD plugged in with a sata adapter that windows sees fine, and the drive shows in the bios fine but ubuntu doesn't seem to recognize the drive (doesn't display in hardware info even though I see the sata controller was deteected.

specs

Foxxcon Nforce 6100 chipset MB
Opteron 144 Proc
1gb of ram

DVD and 30 gb HD on IDE CHannel 0
2x250gb on CHannel 1

both those detect

and on the first Sata channel I have my 250gb with the IDE to Sata adapter.

anyone have any ideas? i'm fairly new to linux, but learning fast

---

### Post by Yellow Pasque on 2008-02-11
Look in your system log to see if you can find any mention of the drive. (Type dmesg in the terminal).

Also, run lshw to make sure your system isn't seeing it.
```
sudo lshw -businfo -C disk
```

---

