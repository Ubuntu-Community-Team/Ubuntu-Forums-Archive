---
title: "Hard Drive Performance"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by ender7007 on 2007-07-29
Hello all:

Here's my situation.  I have a brand new Dell d620 laptop that I'm running Feisty x64 on.  The systems works pretty well, but I seem to have odd periods where my system shows high CPU usage and the CPU appears to be waiting for I/O.  This leads me to believe that I could have my HDD setup better.

I've looked at hdparm, but it doesn't seem to be able to adjust any of the parameters for my HDD because the OS believe my HDD is a SCSI device and gives it a /dev/sda device.  

Some other information, I have 1GB of RAM but I'm not using swap.

I am using VMware Server and running a Windows XP guest but at the time of the high I/O Wait, the VM isn't doing anything.

Is there any scsi tools I can use to tune this device?

Are there any programs that will tie I/O usage to a PID?

If anyone has any ideas that might help I'd be very grateful.

Thanks,

Aaron

---

### Post by Dokatz on 2007-07-29
You need swap, It helps tremendously man. Try re-partitioning with some swap space...

My hard drive is a sata drive and is listed as /dev/sda as well...And it works just fine. I don't think that means that ubuntu assumed it was SCSI

---

### Post by ender7007 on 2007-07-29
Sorry to mislead.  I meant that I have swap, but the system isn't needing to use it, so my RAM isn't overloaded....

---

### Post by ender7007 on 2007-07-29
BTW, Mont Vernon!!  I've been through there a few times on my way to Crotched Mountain.  Very scenic town.

:)

---

