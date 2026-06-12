---
title: "Kubuntu Install and Live CD hangs on Boot: IO Probe 0x100-0x3af"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by thommy.oster on 2007-02-10
Hi
I'm trying to install Kubuntu on a Medion Speedmaster Notebook (MD40700).
When trying to boot the CD (both, Install and Live CD) the system hangs with 

"cs: IO Port probe 0x100-0x3af".

If I skip this with "reserve=0x100,0x3af", Kubuntu can't find my CD-Drive (because IDE1 is on IO 0x170-0x177, 0x3somthing...
I don't really know much about Linux, so I just tried "reserve=0x100,0x120", it hang again.... with reserve=0x100,0x140 it booted, but couldnt find the CD-Drive aswell.
In all reports I saw there were lines like 
"cs IO Port probe 0x100-0x3af, excluding 0x170-0x177".

Can somebody help me? Is there another Command as "reserve=iobase,extend", which I have to use?....

Note: The Ubuntu 5.04 CD boots without any problems...

---

