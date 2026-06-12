---
title: "/dev/hiddev0: works in fedora, not in ubuntu"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by haploid on 2006-10-09
Here is our problem:

We have a postal scale connected via usb to our shipping stations. Under both fedora core 3 and ubuntu 6.06.1 they are recognized by the kernel and assigned to /dev/hiddev0

On the FC machine, running "cat /dev/hiddev0" results in the screen filling with data, which is the desired result. Our apps process this data stream just fine.

Doing so on the ubuntu machine, however, results in no data at all, and our apps are also unable to get any data from /dev/hiddev0.

The hardware in question is identical. The output from lshal is identical. The kernel messages in /var/messages are identical. The only difference is FC versus Ubuntu.

Can anyone explain this strange behavior? Thanks.

---

