---
title: "(Ubuntu Server 6.06 LTS) Add a new unpartitioned HDD"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by elnigno on 2007-09-10
Hi everyone!
This is my first post in the Ubuntu Forums, I think I will post many others since I plan to use Ubuntu more and more in the next months :)

Now, to the point. I have and old pc (PIII 550Mhz, 128Mb ram) that I want to use as home server. So I installed Ubuntu Server 6.06 LTS on the main HDD (6Gb) and so far no particular issue showed up.
I bought a new internal HDD (500GB, IDE) to increase the storage and inserted it in to the system, but I cannot find it in /dev, so I cannot partition or format it.

Now, I have never added an internal HDD to a desktop, I don't know exactly the meaning of master/slave and so don't know what is the best setting for my case; more over, even if I am not a complete beginner with Ubuntu and Linux, I have never used the command line very much, as it is required in Ubuntu Server.

So, can someone tell me what should I do, step by step, to add this new HDD to my server?

Thank you very much for helping me!

---

### Post by logos34 on 2007-09-10
The jumper on the back of the drive should be set for 'slave' (or 'cable select' if that is how the 6GB drive is configured).  There might be a sticker on the drive indicating which pins to use; if not, consult the manual or the docs on the manufacturer website.

Go into your Bios at startup (press F2, F12, Delete, whatever) and check the hard disk detect settings...should be set to [auto]

---

### Post by elnigno on 2007-09-10
Thank you very much, it worked!
The sticker on the drive didn't tell how to set the jumper to Slave but the manufacturer site does :)

---

