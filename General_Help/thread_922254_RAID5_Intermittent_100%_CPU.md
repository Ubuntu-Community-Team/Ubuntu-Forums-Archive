---
title: "RAID5 Intermittent 100% CPU"
date: 2008-09-17
forum: General Help
---

### Post by MilkeySUFC on 2008-09-17
Hi,

I have a problem with intermittent 100% CPU utilisation with a box I am trying to set up with RAID5.

System spec:
AMD 3600 X2
ASRock 939N68PV-GLAN, 4x Onboard SATA-II
1x 1Gb Corsair RAM
1x 40Gb IDE system drive (ext3)
Ubuntu 8.04.1

In this config everything works perfectly CPU utilisation about 3-10% each core with just system monitor running. No freeze issues.

I then added the RAID5 disks:
3x 500Gb Hitachi SATA-II, 7200RPM, 16Mb cache

I used the LiveCD to partition & format (ext3) each of the 3 drives.

I installed mdadm and created the software RAID5. Everything looked fine. I have a 931Gb disk available.

My issue is that CPU utilisation is 20-35% on each core with just system monitor running but, at irregular intervals (between 2 to 10 minutes), spike to 100% on both cores and freeze the system for 2 or 3 seconds. This doesn't seem to affect operations on this machine which carry on quite happily (screen greys out, system monitor hangs, then when it comes back shows the frozen time as 100% on both cores).

When a freeze occurs:
Copy to/from networked Ubuntu PC carries on okay.
Copy to/from networked Windows PC fails with connection lost.

Does anyone have any ideas what could be wrong or how to go about fixing it?

---

### Post by Trebaruna on 2008-09-17
Have you run top to identify the process(es) gobbling up the CPU? You might want to include that info and/or search for known problems with those processes.

---

### Post by MilkeySUFC on 2008-09-17
> **Trebaruna said:**
> Have you run top to identify the process(es) gobbling up the CPU? You might want to include that info and/or search for known problems with those processes.

How can I do that? I don't know a CLI command to do it.

System monitor shows high % utilisation but processes list doesn't show any processes eating up that much cpu.

---

### Post by bingoUV on 2008-09-17
Then it is most likely kernel utilization of CPU, most likely IO. Install iotop, and run it in terminal as root. It will show the top processes causing IO.

```

sudo apt-get install iotop
sudo iotop

```

---

### Post by MilkeySUFC on 2008-09-17
> **bingoUV said:**
> Then it is most likely kernel utilization of CPU, most likely IO. Install iotop, and run it in terminal as root. It will show the top processes causing IO.

```

sudo apt-get install iotop
sudo iotop

```

Great, thanks. I'll have a pop at that when I am at the machine tomorrow.

---

### Post by fjgaude on 2008-09-19
Where does one get iotop... it's not in the Ubuntu repository.

Okay found it:

[http://packages.debian.org/sid/all/iotop/download](http://packages.debian.org/sid/all/iotop/download)

Thanks!

---

### Post by MilkeySUFC on 2008-09-22
> **MilkeySUFC said:**
> Great, thanks. I'll have a pop at that when I am at the machine tomorrow.

Well, after leaving the machine on 48 hours, when I next had a chance to get to it, the "freeze" issues seem to have disappeared. After rebooting, it happened once after about 10 minutes and hasn't happened since (that I've noticed). Thanks for everyone's help anyway.

---

