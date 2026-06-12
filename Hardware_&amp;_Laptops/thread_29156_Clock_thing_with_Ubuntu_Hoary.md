---
title: "Clock thing with Ubuntu Hoary"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by Peter Mount on 2005-04-23
Hi

I loaded Ubuntu Hoary on my other hard drive. I have two hard drives, each in their own caddy so I just have one in at a time.

I did notice after I loaded Ubuntu Hoary that the clock was slow by 2 hours so I adjusted it accordingly. After I swapped hard drives I noticed the clock was fast by 2 hours in Windows.

Has anybody else noticed this with their computer clocks? Is there a patch for this?

By the way, I did notice that Ubuntu is a tad slow on my machine, but still quite usable so far. I haven't used it thoroughly though. I did play mine sweeper and I noticed a delay in playing that game that I don't experience in Windows but I am hoping to get a new confusor later this year so I'm not to worried.

Thanks

Peter Mount
[email]info@petermount.au.com[/email]
Pentium 2-350
448 Mb PC-100 SDRAM
64 Mb ATI Radeon 7000 Video card
Gygabyte BXC Motherboard

---

### Post by andvaranaut on 2005-04-23
Hi Peter 

Ubuntu, by default, uses UTC time on the clock. If you share the clock with other OSes which do not use UTC, there will be some juggling of the times. Furthermore, as Ubuntu syncs itself with a remote time server via NTP on each bootup, the clock will be slow again if you boot Ubuntu and then Windows.

The solution is not using UTC, but localtime, on the clock. Edit the file /etc/default/rcS and change the line reading **UTC=yes** (or just **UTC=**) to **UTC=no**. Reboot and adjust the time. That should do the trick.

Good luck!

---

### Post by ultima2k on 2005-04-23
I had that problem too some days ago so I simply changed the timezone to some place that were 2 zones away :p

---

### Post by DirtDawg on 2005-04-23
[QUOTE=ultima2k]I had that problem too some days ago so I simply changed the timezone to some place that were 2 zones away :p[/QUOTE]

HA! I love it. Thats exactly the type of "jimmy-rigging" I do all the time.

---

