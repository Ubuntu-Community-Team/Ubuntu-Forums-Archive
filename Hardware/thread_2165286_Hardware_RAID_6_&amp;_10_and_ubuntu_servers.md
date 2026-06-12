---
title: "Hardware RAID 6 &amp; 10 and ubuntu servers?"
date: 2013-08-04
forum: Hardware
---

### Post by ericmachine on 2013-08-04
Hi everyone,

I am buying 2 servers which both setup as follows:-

Server A - RAID6

Server B - RAID10

Both these servers will have a hardware raid controller
LSI 2108 RoC SAS 6Gb/s internal channel IOP RAID Controller with 512MB cache supporting RAID level 0, 1, 5, 6 ,10

My questions:-

a. Does RAID6 and RAID10 will do the disk replication automatically for me? 
b. If not, do I need to configure extra things when install Ubuntu 12.04 LTS 64 bits?
c. If hardware raid does automatically, how can I know whether my Hard disk 1 gets replicated to Hard disk 2?

Any help? Thanks.

---

### Post by tgalati4 on 2013-08-04
When you boot your server, you should see a RAID BIOS in addition to your normal computer BIOS.  On Dell servers, typically, Control-S during boot will bring up RAID BIOS.  Look through the options and share them here.  Typically, you specify the type of RAID you want to create and the hardware takes care of it--no further work needed on your part.  No configuration is required within Ubuntu.  You do not use software RAID (mdadm) when using hardware RAID--although you probably can, there would be no benefit to using it.

For question c, you specify which drives are in the RAID when you set them up in the RAID BIOS.  Read any documentation provided by the vendor so you know exactly how the hardware RAID is supposed to work.  There are many variations of RAID hardware and many differences in capability.

---

### Post by ericmachine on 2013-08-04
Thanks so much for replying back :)

If hardware raid handles all, how would I know it does replicate? Is there a way to see the status of replication?

Any help? Thanks.

---

