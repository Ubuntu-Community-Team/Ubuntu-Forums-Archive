---
title: "Edgy detected my IDE HDD as HDA - Fiesty sees it as SCSI (SDA)?????"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by tact on 2007-04-25
Hi all,

I have a Dell D410 with one (only) inbuilt 75GB HDD.   When I was using Edgy it was seen as HDA, an IDE drive which I think is correct.  

I tried to use the upgrade manager to upgrade to Fiesty but it failed before it really got started so I downloaded the Desktop LiveCD ISO and installed "clean" from that.  (root is on a separate partition).

The liveCD install completed no issues.  The laptop is working and everything seems to work fine.  But is it peculiar or what that Fiesty detected the HDD as a SCSI drive and so it is named SDA and all the partitions follow suit.

Is this a bug?  Is it a bonus?  Anyone got ideas?

---

### Post by reiki on 2007-04-25
Not a bug. I don't claim to fully understand it, but Feisty does basically see all of your drives as scsi according to YOUR (our?) way of thinking. I have a single IDE drive and 2 SATA drives. With Edgy, they are hda, sda, sdb.

With Feisty, they are sda, sdb, sdc. It's fine. Everything works. :)

---

### Post by Rinzwind on 2007-04-25
It's by design. Read this and you'll know why: 
[https://wiki.ubuntu.com/LibAtaForAtaDisks](https://wiki.ubuntu.com/LibAtaForAtaDisks)

---

### Post by tact on 2007-04-25
Ahhhh ok - so its by design.   Thanks for easing my mind.  :)

---

