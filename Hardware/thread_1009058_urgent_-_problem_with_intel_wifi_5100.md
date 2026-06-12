---
title: "urgent - problem with intel wifi 5100"
date: 2008-12-12
forum: Hardware
---

### Post by eltharynd on 2008-12-12
hi everyone...

I recently bought an "acer aspire 5930" with an "intel wifi link 5100 AGN",
the pc is fantastic, but it came with windows vista home pro.

So when i first had it I installed ubuntu 8.04 in dual boot.
That's when I realized drivers for my wireless card didn't yet exist... so I formatted ubuntu's partition and worked only with vista.

Now that Ubuntu 8.10 as come i first formatted the whole hard disk and completely switched to ubuntu. 
But now I realized that I'll need to work on windows too at school..

So then I formatted again and installed vista, the problem is: when I boot vista my wireless card won't work...

My system sees it, I can install drivers from windows update ( i tried those and also certain from intel/acer/other websites) but my wireless card doesn't see any wireless network.
In addition if I try doing a manual connection it says an unexpected error as come just when I begin the process.. 

So i installed ubuntu in one of my partitions, and just before the OS was even fully loaded my wireless card detected my home network -_-

My guess is: (even if they're just theories because I'm no expert of Ubuntu)
Ubuntu installed custom firmwares on my wireless card, which is now not working with vista anymore.

So, please I need wifi with windows at school, someone of you knows how to fix it?

---

### Post by iponeverything on 2008-12-12
Firmware is loaded on fly in both vista and linux.

look in /var/log/messages for:

firmware: requesting <your firmware>

Try getting the latest drivers for vista:

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3062&OSFullName=Windows+Vista*+Home+Premium%2C+32-bit+version&lang=eng&strOSs=153&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3062&OSFullName=Windows+Vista*+Home+Premium%2C+32-bit+version&lang=eng&strOSs=153&submit=Go)!

---

### Post by eltharynd on 2008-12-12
I can't count how many times I tried... It's just not working :( nobody got clues?

---

### Post by eltharynd on 2008-12-12
i know for sure it's not an hardware problem, cause with ubuntu it works.... but it won't work in vista :/

---

