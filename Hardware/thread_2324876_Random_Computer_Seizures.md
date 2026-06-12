---
title: "Random Computer Seizures"
date: 2016-05-17
forum: Hardware
---

### Post by peter_thompson2 on 2016-05-17
System - 
Dell Inspiron 
Dual Core E5200 2.5Ghz CPU
AMD RV730 1GB Video Card
4GB RAM
1TB HDD
DVD Writer

Software installed and running-
Flexget
Transmission
NZBDrone
Couch Potato
MYSQL
Wordpress

Symptoms - 
At random (I have not been able to establish a pattern) the machine will become unresponsive and will require power cycling to reboot.

The machine had Ubuntu 15.04 desktop installed and ran flawlessly.

The issues began when I set up a crontab entry to CP files from a local drive to a network share. (Share was established in fstab and did not require permissions).

The command worked happily. 

When the issue appeared, I removed the crontab entry but still got random lock ups.

I updated everything using sudo apt-get update and read that it was wise to look for new kernel versions. I enabled that and the system started updating to 16.04.

After the reboot, I had information on screen about fsck journals and orphaned nodes. Machine would not boot further.

Fearing that it was a HD issue/bad blocks, I obtained another 1TB drive, and downloaded the 16.04 distro. Performed a complete rebuild including installation of the original software packages.

Although less frequent, I'm still getting random lock ups.

I've even tried changing the SATA cable and connecting to a different SATA port on the motherboard - no difference.

Any ideas/suggestions/tips before I pull out what is left of my hair?

Thanks

---

### Post by Yellow Pasque on 2016-05-17
- Run memtest
- Keep an eye on temps and don't hesitate to get some computer duster spray and give the system (especially the heatsinks/fans) a good spring cleaning.

---

### Post by mastablasta on 2016-05-17
might be a good idea to check the logs as well. (/var/log)

---

### Post by weatherman2 on 2016-05-17
I agree with the advice about Memtest and monitoring temperatures.

If the Dell has integrated video (so you could remove the AMD video card and still use the PC), try removing it temporarily and see if that improves things.

Also look carefully at the motherboard for leaking capacitors - that is, capacitors that look like they have kind of exploded and maybe bubbling with grown goo.  To learn more, do a web search for "blown caps" and you'll find lots of pictures.  If you have blown caps, most people would recommend replacing the motherboard, though some brave souls might attempt to replace the bad caps.  Personally, I wouldn't.

---

