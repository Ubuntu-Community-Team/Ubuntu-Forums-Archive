---
title: "Cannot boot from Ubuntu 9.04 CD"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by fredwong on 2009-04-29
I am trying to upgrade to 9.04 from 7.10 but I am getting these message when booting :(:confused::confused:

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

Loading, please wait....
    9.192020] hub 5-0:1.0: Cannot enable port 2. Maybe the USB cable is bad?
   12.280019] hub 5-0:1.0: Cannot enable port 2. Maybe the USB cable is bad?
   15.368015] hub 5-0:1.0: Cannot enable port 2. Maybe the USB cable is bad?
   18.456019] hub 5-0:1.0: Cannot enable port 2. Maybe the USB cable is bad?
   18.456082] hub 5-0:1.0: Unable to enumerate USB device on port 2

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7)..............
........

initramfs)


I have AMD X2 64bit 2.6GHZ CPU

---

### Post by kpkeerthi on 2009-04-29
Are you trying to boot with the 9.04 live CD? Or performing a online upgrade?

If you are trying to boot with the Live CD, you might to select "Check CD for errors" from the CD boot menu. If the check fails, try burning a new CD at speed not more than 4x. Also verify the md5sum of the downloaded ISO.

---

### Post by fredwong on 2009-04-30
Both live CD and fresh install gave me the same messages on my Ubuntu HTPC (Gigabyte GA-MA69G-S3H, ADM x2 64bit 5000+ 2.6GHz, 2g RAM). I will try your suggestion of burning another CD. Although I am not quite convinced that broken CD burn is the issue because I got the same error messages from Mythbuntu 9.04 as well. The strange thing is I can boot into Mythbuntu on my Sony Laptop but the standard Ubuntu won't budge.

Thanks in advance for any other suggestion.

---

