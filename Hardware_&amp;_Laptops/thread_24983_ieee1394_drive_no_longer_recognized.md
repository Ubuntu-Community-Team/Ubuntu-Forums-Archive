---
title: "ieee1394 drive no longer recognized"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by msmith on 2005-04-08
Hi all, 

This is an issue that just developed. It was being recognized and automatically mounted until an incedent where I had a power outage that caused the system to shutdown without unmounting. Since then, it isn't showing up in device manager at all. The drive itself is ok. I've mounted it my iBook, Any suggestions?

---

### Post by msmith on 2005-04-08
UPDATE:

Ok, That's wierd. It spontaneously started working again. Last time I rebooted, I did it with the drive plugged in and turned on, with te same (non)result as when booting with it unplugged, or with it plugged in but off. Went back to gazing at the tail of /var/log/syslog, turned the drive off and then on again, and bingo. dirve recongized & both partitions mounted. 

I guess the lesson is to always unmount it before shutting down and not to keep it mounted when it isn't needed in case of a power outage.

---

