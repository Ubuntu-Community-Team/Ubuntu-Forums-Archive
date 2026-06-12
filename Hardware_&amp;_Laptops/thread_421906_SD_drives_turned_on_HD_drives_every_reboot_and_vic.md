---
title: "SD? drives turned on HD? drives every reboot and viceversa"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by ghoshe on 2007-04-24
I have this strange problem, every time I reboot my computer SD? devices are turning into HD? devices, I say for example

now ->/dev/sdYX 
rebooting ->/dev/hdZX 

where Y and Z are specification device letters, and X partition numbers.

Even SATA disks are recognized like HD? sometimes. That's SOOOO spooky.

I can't find any solution. I can boot the system because the UUID mounting (phew!)

I have a SIS based motherboard with SIS based SATA Raid controller.

Thanks for answering!

---

### Post by macogw on 2007-04-24
I thought everything on Feisty was /dev/sd*

Why all the ? mid-sentence?

---

### Post by ghoshe on 2007-04-25
Yes, i know that feisty uses libata for accesing drives, the problem is that the device name of my drives is changing every reboot, so all the applications that use the device name to get information, like hddtemp, are not working well, i mean, if i configure my system to get smart info from my system HD, and it is /dev/sda, after the next reboot it changes to /dev/hda or hdb or hdc, after rebooting again it changes again to sda, or not :P , the same occurrs with all the other drives in the system.

---

### Post by ghoshe on 2007-05-04
C'mon nobody has the same problem??

My motherboard must be possessed by a demon or something :P

---

### Post by gwi on 2007-10-29
I am having the same kind of problem. Sometimes my (only) harddisk is assigned /dev/sda, sometimes it is assigned /dev/sde (and sda up to sdd are assigned to the card reader).

In the sensors-applet hddtemp is configured to show the temperature of /dev/sda. If after a reboot the harddisk is at /dev/sde, hddtemp shows -1 as the temperature.

Why is the harddrive sometimes assigned /dev/sda and sometimes /dev/sde?
How can hddtemp be configured so that it always looks at the device assigned to the harddisk?

---

