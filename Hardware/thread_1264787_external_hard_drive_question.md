---
title: "external hard drive question"
date: 2009-09-12
forum: Hardware
---

### Post by interceptorV8 on 2009-09-12
Okay, I saw this:

[http://www.geeks.com/details.asp?invtid=SIL-CA-06-20336-PB&cat=CSE](http://www.geeks.com/details.asp?invtid=SIL-CA-06-20336-PB&cat=CSE)

My question:

If I were to buy this and put two 1-TB drives would ubuntu acknowledge it as ONE disk in jbod/spanning mode or two separate disks?

I dual boot with vista and ubuntu 9.04 and am looking for an inexpensive way to backup and/or consolidate my collection of hard drives (4 external/2 internal).  My computer is not set up for any kind of RAID array nor do I know how to go about setting one up...

---

### Post by rob-ward on 2009-09-12
It will definetly do JBOD but I am not sure about raid, I think you best bet would be to setup software raid in ubuntu, to do that you have to install using the alternate cd or convert your existing drives(not sure how to do that never tried) setting up a raid mirror from the alternate cd isn't that difficult, you may want to have a play at setting one up in virtualbox first though so you know what you are doing. Don't think that the external caddy will have any advantage over software raid.

---

