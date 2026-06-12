---
title: "Desperate: Need FN key drivers for Sony Vaio VGN-FZ140E running XP"
date: 2009-06-12
forum: Hardware
---

### Post by morland on 2009-06-12
I need to use use my laptop with a beamer/projector and turns out that the function key (F7) does not work **since I am running XP**. I need a solution desperately and can some please help me get just the right drivers/software/whatever is needed to that I can use the function keys (especially the one for F7 i.e. for external monitor/beamer/projector).

Many many billion thanks in advance.

---

### Post by prcjac on 2009-10-14
Hey, I expect this is a bit late but he's some advice for the future.
You need to make sure you have these 4 things installed for Sony FN keys to work under XP
1) Sony Firmware Extension Parser driver installed or the SPIC Driver installed
2) Sony Shared Library installed
3) Sony Setting utility series
4) Vaio Event service
These can be found here:
[HERE]("http://www.sony-asia.com/subtype/usefulinfo/asset/216869/productcategory/it+personal+computer")
Or
[HERE]("ftp://ftp.vaio-link.com/PUB/VAIO/ORIGINAL/")
It's best to reboot after each installation just to make sure.
This should re-enable FN key control.
To enable brightness control you need to install the correct driver. Vaio Power management and the Intel GMA drivers should sort brightness on any Intel graphic chipset machines.
Otherwise, Vaio Power management and nVidia drivers from [here]("http://www.laptopvideo2go.com/")

Hope that helps

---

### Post by morland on 2009-10-16
Many many thanks. However I visited the URL and am confused and don't know what to download. I could not find the 4 items suggested by you on the web site. Can you kindly help me exactly identify what I need to download. Just to remind: my model is VGN-FZ140E.

Thanks.

---

### Post by prcjac on 2009-10-28
No problem, sorry that I've taken so long to reply.
I use a Vaio FZ myself and I've managed to get XP running nearly perfectly with the Vaio Drivers.
The Sony Firmware Extension Parser is [here]("ftp://ftp.vaio-link.com/PUB/VAIO/ORIGINAL/SFEP%20DRIVER%20SONY_8.0G_8.0.0.1.ZIP") so download it and extract it
Open Device manager and find the Unknown Human Interface Device or similar and update the driver with the extracted files.
The Shared Library is [here]("ftp://ftp.vaio-link.com/pub/OS/XPDOWNGRADE/1_SONY%20SHARED%20LIBRARY%20FOR%20XP%202.10%20_%202.10.00.ZIP"),again extract the files and install the software, then reboot the machine.
The install the Setting Utility from [here]("ftp://ftp.vaio-link.com/pub/OS/XPDOWNGRADE/3_SETTING%20UTILITY%20SERIES%201.8%20_%201.8.00.ZIP")
Reboot and finally extract and install Vaio Event service from [here]("ftp://ftp.vaio-link.com/PUB/VAIO/ORIGINAL/VAIO%20EVENT%20SERVICE%204.1%20_083Q_%20%204.1.00.07150.ZIP").
Reboot and fingers crossed your function keys should work.

The latest powermanagement software is [here]("ftp://ftp.vaio-link.com/PUB/VAIO/ORIGINAL/VAIO%20POWER_MANAGEMENT_3.2_091Q_3.2.0.10310.ZIP"), but an older copy is [here]("ftp://ftp.vaio-link.com/PUB/VAIO/ORIGINAL/VAIO%20POWER%20MANAGEMENT%202.4_%202.4.00.15100.ZIP") if there are compatibility issues.
As for the graphics drivers, you will still find them in the previous link. If you need any instructions on that just reply back.
I hope that helps,
Best wishes

---

### Post by morland on 2009-10-28
Thanks prcjac. Will download these and give them a try.Will post back with progress.

Many thanks.

---

### Post by morland on 2009-10-29
> **prcjac said:**
> 
The Sony Firmware Extension Parser is...
so download it and extract it

Open Device manager and find the Unknown Human Interface Device or similar and update the driver with the extracted files.


Hi prcjac,

Hope you get the time to reply. 

I downloaded all the files but got stuck at the very 1st step. I went to My Computer | Properties | Device Manager but could not find Unknown Human Interface Device.

Can you kindly guide in this regard so that I can proceed.

Many thanks in advance.

---

### Post by prcjac on 2009-11-06
Hi sorry for the late reply,
Ubuntu forums don't email me when I have someone reply to a thread.
Anyway, I had a play around with my XP partition and found that the Firmware extension parser drivers I recommended don't work on XP.
However these will, visit [http://www.sony-asia.com/support/download/240680/sectionfirst?subpage=detail](http://www.sony-asia.com/support/download/240680/sectionfirst?subpage=detail) and download and install the SonyNC Device Upgrade Driver, the Sony Shared Library, the  VAIO Event Service and the Hotfix and the Settings Utility.
Now you should be able to get the FN keys mostly working, they're not perfect but the Fn F7 key should do.

I hope that helps

---

