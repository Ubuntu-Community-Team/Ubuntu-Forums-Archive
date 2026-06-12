---
title: "8 drives failed simultaneously in server."
date: 2014-11-30
forum: Hardware
---

### Post by ads2996 on 2014-11-30
Hi, 

My server was starting the moment power was connected and running the fans at full speed then shutting down due to insufficient fans,  I eventually fixed  this the connectors weren't seated properly. Then when I got it booted back up all the drives were orange, indicating they had filled and had been placed offline by the raid controller. I placed them in another server and they also showed as failed. I thought it was weird for them all the fail. Other droves work in the first server. I was wondering is there anyway to resurect these drives? 

Thanks in advance.

---

### Post by tgalati4 on 2014-11-30
If you are using a hardware-based RAID controller, then you need to boot into the RAID's BIOS and examine the status of the pool.  Usually you will be presented with some options to recover and which drive in the pool has failed.  Try Control-S during boot and see if the RAID BIOS comes up.

---

### Post by ads2996 on 2014-12-01
I have checked the raid bios but it doesn't show any logical or physical drives in it

---

### Post by tgalati4 on 2014-12-02
Perhaps your hardware RAID controller has failed.  It is unlikely that 8 drives have failed and your CPU is still functioning (from a lightning strike for instance).  Some hardware RAID cards have a battery for cache protection.  Test it and replace it if necessary.

Look for your manufacturer's diagnostic CD.  Download and burn it and run through the tests.

It's also possible that your RAID card has corrupted your disks in a major way.  In that case, you would need to use your disk manufacturer's utilities to perform a diagnostic and low-level format to make the drive usable again.  If this works, then do the same for the other 7 drives.

Of course you have lost your data, but RAID was never intended as a backup strategy.

Check the SMART status of each individual drive to determine if any particular drive has failed.

---

