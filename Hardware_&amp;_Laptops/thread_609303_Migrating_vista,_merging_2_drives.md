---
title: "Migrating vista, merging 2 drives"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by TV-VCR on 2007-11-10
[IMG]http://img260.imageshack.us/img260/613/computernk3.png[/IMG]
This is what I want to do:

Merge drives E: and D: as a JBOD. Question - does the D975XBX2 support making a JBOD? And where can I find the drivers for it? And how do I do it?

Migrate Vista from C: to D: (which would be both drives E and D). How do I do this?

Rename D: to C:, and C: to D:

Install Ubuntu on D:

Thanks in advance.

---

### Post by basotl on 2007-11-10
A quick reference on your mother board shows me that your board has a RAID controller but doesn't have too many details on it. Consult your motherboard manual for details. I would highly suggest against a JBOD or Spanning set up. It really doesn't offer any improvements in speed and harms redundancy.

It would be a better idea to migrate your data to the desired drives and then set up Ubuntu on the drive of your choice. 

Gparted [http://gparted.sourceforge.net](http://gparted.sourceforge.net) is a good tool for copying data and setting up the partitions you need.

---

### Post by TV-VCR on 2007-11-10
> **basotl said:**
> A quick reference on your mother board shows me that your board has a RAID controller but doesn't have too many details on it. Consult your motherboard manual for details. I would highly suggest against a JBOD or Spanning set up. It really doesn't offer any improvements in speed and harms redundancy.

It would be a better idea to migrate your data to the desired drives and then set up Ubuntu on the drive of your choice. 

Gparted [http://gparted.sourceforge.net](http://gparted.sourceforge.net) is a good tool for copying data and setting up the partitions you need.

I need Ubuntu installed to use that, unless there is a Windows version of it, correct me if I'm wrong.

And I want to install Ubuntu after I have the rest of the stuff set up. :)

---

### Post by basotl on 2007-12-19
> **TV-VCR said:**
> I need Ubuntu installed to use that, unless there is a Windows version of it, correct me if I'm wrong.

And I want to install Ubuntu after I have the rest of the stuff set up. :)

Sorry for not noticing your reply. The link I pointed you too has a live CD for helping with that. It's OS independent.

---

