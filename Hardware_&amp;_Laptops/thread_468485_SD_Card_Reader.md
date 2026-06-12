---
title: "SD Card Reader"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by darkzim on 2007-06-08
I have a Compaq Nc4000 notebook which runs Edgy....  For some reason, my built-in SD Card reader won't work... I have researched the topic and have found a lot of information on the TI readers, but no such luck with my "02 Micro, Inc" reader.  

"sudo modprobe tifm_sd" doesnt work..

I tried putting tifm_7xx1, tifm_core, and tifm_sd in /etc/modules and rebooting, but no luck...

Does anyone have any experience with this?

Here's the relevant in lspci:

> 00:0b.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:0b.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:0b.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator


---

### Post by darkzim on 2007-06-11
-bump- anyone?  I'm kind of desperate because I'm on an exchange program to Japan right now (I m a high school student from america) and would really like to get this working so I can upload pictures off my camera to show people ^_^.

---

### Post by Offoffoff on 2007-08-04
Hello!
I have the same laptop. And cannot use SD slot too...

---

### Post by lingnoi on 2007-08-05
Its broken on my laptop too. It used to work when I upgraded from Edgy but once I did a full reinstall of feisty it has broken.

Laptop support is going so downhill now...

---

### Post by Offoffoff on 2007-08-05
Maybe the best way to fix it is to send letters to HP-support?

---

### Post by HarshReality on 2007-08-05
> **Offoffoff said:**
> Maybe the best way to fix it is to send letters to HP-support?

No offense but your a bit of a smartalec.... last 3 times I contacted HP support via email or phone I got an arabic gent who actually asked "What is Linux". When I explained it was an alternative free OS to use instead of windows I was told "Your device is built for windows only, linux is not supported" so I found a link that was an HP laptop with linux and then he finally just choked up and said "Sorry we cannot support your device".

Bottom line, DELL, HP, GW and all are exactly the same. They made the pitch, got your money and then to hell with you.

---

### Post by mlcooper on 2007-12-17
I'm in the same boat with a HP NC4010 unit.  Any chance someone has this working?

---

### Post by mlcooper on 2007-12-17
FYI - Emailed O2 Micro about getting a driver for this unit.  Here's the thread:

I am looking for a linux driver for your O2 Micro, Inc.
OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20).  Most of the web
forums state that your company has chosen not to release a linux driver
at this time.  If there is one available, please let me know where I can
download a copy.  Otherwise, I encourage you to please support the open
source community and make a driver available.

Having to keep a Windows XP installation on my disk drive just to ready
my digital camera's SD card is a real pain, marginal security threat and
frankly against my political beliefs as an OSS advocate.

Thank you for your time and consideration.  Have a very Merry Christmas
and Happy New Year!

To which they responded:

Dear Mr. Cooper,

We do not distribute Linux drivers for the M1/MC1 product.  It is an
old product, and the architecture of that part is complex; whereas
the Windows driver contains many system-specific elements.  We will
not distribute code that may lead to data loss or corruption; thus,
it is a difficult situation to support open source.

Additionally, our driver codes are based on source that we licensed
from 3rd parties, and our licenses do not include distribution rights.

We provide Linux drivers for new products, and understand your need.

Regards,
Neil Morrow

---

### Post by Offoffoff on 2008-06-15
> our driver codes are based on source that we licensed
from 3rd parties, and our licenses do not include distribution rights.
Technological progress will stop soon due legal walls... I have only one hope - Linux.

---

