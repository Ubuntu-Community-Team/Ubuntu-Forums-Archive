---
title: "SMART test: one failing attribute: bad blocks; drive claims to be OK"
date: 2017-01-18
forum: Hardware
---

### Post by jdkcarlson on 2017-01-18
I'm running Ubuntu 16.04 on an Acer Aspire laptop, although I suspect my question is more generic. My hard drive says it passes the SMART self-test when I run it out of the Disks application, but that one attribute is failing, namely the runtime-bad-block-total, but that that still means the disk is OK. I first noticed there was something up with this number last year, and it keeps increasing, thus:

Sept 2016:  2162694
14 Oct 2016: 2490375
29 Oct 2016: 2686984
19 Nov 2016: 2949129
6 Dec 2016:  3145737
16 Dec 2016: 3276809
27 Dec 2016: 3407882
7 Jan 2017:  3538954
14 Jan 2017: 3604490

I want to take my drive's word it's fine, but these numbers seem alarmingly large, and it's of concern that they keep increasing; even I am aware there must be some upper limit. 

Another thing that periodically happens is that I can't type in a document or save anything; this means the drive has decided to become write-only because the directory structure has become damaged. When this happens, something called BusyBox appears, but I don't know what to do with that, so I boot off a stick instead and run ```
 fsck -y
``` on my device's Ubuntu partition, and it runs fine again after reboot. But this has happened a few times now and I'm worried it could be related to drive failure.

1. **How much peril am I in?**
2. **What should I do now?**

---

