---
title: "feisty on asus A8JM:kernel ata driver problem"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by stiffme on 2007-04-20
my kernel is 2.6.20-15-generic
my laptop works fine on edgy and dapper.
when i use feisty, my system freezes from time to time. Every time it freezes, I have to wait for about half a minute, and then i work fine again.
Then i enter a console , and kernel showed the following output:
ata1: failed to respond(30 secs, status 0xd0)


sometimes kernel showed :
ata1.01:exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata1:01cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in


I have a PATA harddisk ,but in feisty, my hard disk is recognized as /dev/sda
I tried to compile kernel source of version 2.6.20 from kernel.org, this problem remains.

PS: I am using ICH7, in feisty, at first ,no sound is out. But actually kernel detects my sound card and is LOOKS fine. The Only problem is NO sound out. Then i compiled the alsa driver and lib from alsa website, and the problem is resolved.

Sorry for my English.I am not good at it.

---

### Post by stiffme on 2007-04-20
I checked my hard disk ,nothing wrong.

---

### Post by Murilo on 2007-04-23
I had the same problem with kernel is 2.6.20-15-generic on my acer aspire. Then I'm still using the old kernel and it is ok.

I tried everything, inclunding the tutorial posted on other threads. Nothing happens.

---

