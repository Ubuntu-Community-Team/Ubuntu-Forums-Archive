---
title: "drivers for MegaRaid 8208 needed"
date: 2012-04-26
forum: Hardware
---

### Post by TPizza on 2012-04-26
Hello,

I am not a very experienced Ubuntu user, at least not related to hardware and driver issues.

I have the following problem. Here is a machine which apparently has an MegaRaid 8208 ELP Raid controller. A couple of drives are in, forming a raid 5.
I installed ubuntu 12.04 on a different internal drive. This worked. But it seems that ubuntu has no drivers for the raid controller. The manufacturer offers drivers for Suse Enterprise and Red Hat, but not for suse or debian.

I found several topics on different websites, but some lack working links, some lack actual info on how to do things.
If I enter lspci in the console, it seems to find the controller, theres a line saying:

> 03:00.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic MegaRAID SAS 8208ELP/8208ELP [1000:0059] (rev 08)But I have no idea how to access it. I'm a complete newbie regarding raid... never used it.

Oh, and the raid does not show up on fdisk -l. But I think thats normal since it has no drivers installed.

So, does somebody know a way to access the raid? Maybe using the suse oder redhat drivers in ubuntu? Or something else?
Thx.

---

