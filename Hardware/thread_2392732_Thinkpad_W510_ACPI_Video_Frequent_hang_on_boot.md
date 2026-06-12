---
title: "Thinkpad W510 ACPI Video Frequent hang on boot"
date: 2018-05-24
forum: Hardware
---

### Post by dbear2 on 2018-05-24
Using Ubuntu 16.04 LTS.
I have been using Ubuntu on this hardware for almost 3 years. I noted early that the NOUVEAU driver was more reliable than the NVIDIA Quadro proprietary driver. This works most of the time very well. However, I have noted lately that LInux will hang on boot more frequently than it did 3 years ago. (I was using Ubuntu 14.xx lts then) As I watch the boot message the system will hang on the ACPI VIDEO driver message. This affected me perhaps every other boot in the past. However, since the latest round of kernel updates this hang seems to curse me multiple times. Every time I need to do a reboot this hang on boot happens maybe 5 times before I get a successful boot. .  I research the hang issue 2 years ago with the NVIDIA hardware on the Thankpad w510 and didn't find much useful. Still cant seem to find specific mention of this hang. 

My kernel is
Linux XXXXX 4.4.0-127-generic #153-Ubuntu SMP Sat May 19 10:58:46 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

This is a standard W510 -- no special hardware. 

There is an existing thread touching on this here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687910](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687910) 

I was wondering if there is anything else known since Oct 2017 about this -- 
Are there any mitigations, workarounds? Can we control the load order of drivers?

---

