---
title: "Complete copy of hard disk"
date: 2011-04-18
forum: Hardware
---

### Post by claven123 on 2011-04-18
My hard drive is currently too small!  I have a dual boot windows vista and ubuntu machine.  It works fine now.  I just need more space.  I have two options... install a second hard drive (not sure if I can) and how do I make the space available to my current ubuntu install.

Or, the second option is to get a larger HD and make a complete copy of my current one and just replace that with the new one.  Is there a simple way to do this?  I'm thinking I can keep all my settings and programs etc... on the new HD.

Which would be easier/straightforward/less chance of mess ups?

Thanks,

Dennis

---

### Post by Learning Linux 2011 on 2011-04-18
> **claven123 said:**
> My hard drive is currently too small!  I have a dual boot windows vista and ubuntu machine.  It works fine now.  I just need more space.  I have two options... install a second hard drive (not sure if I can) and how do I make the space available to my current ubuntu install.

Or, the second option is to get a larger HD and make a complete copy of my current one and just replace that with the new one.  Is there a simple way to do this?  I'm thinking I can keep all my settings and programs etc... on the new HD.

Which would be easier/straightforward/less chance of mess ups?

Thanks,

Dennis

I think that the copying the smaller HD to the larger HD would be easiest.  There are programs out there that will do just that.  You could always use the older HD for a backup.

If you install a second hard drive you will have some issues to deal with and it could cause some problems for someone who isn't really ready.

If you cannot fit two hard drives in the computer at the same time, you might want to get an external hard drive enclosure to put one of the drives in.

---

### Post by wolfen69 on 2011-04-18
> **Learning Linux 2011 said:**
> I think that the copying the smaller HD to the larger HD would be easiest.

[Clonezilla]("http://clonezilla.org/") will do that, and even has a live CD.

---

### Post by claven123 on 2011-04-18
Clonezilla sounds like a good option.  Are there wiki's or how to's on doing this.  I seen some by googling, but some seem old.   And they don't seem to deal with the dual boot issue of windows and linux.

So, I'll dig a bit more....

I have an older smaller HD, but I'm not sure it will work.  I'll opt to upgrade this HD.

Thanks,

D

---

### Post by sammiev on 2011-04-18
+1 for [Clonezilla]("http://clonezilla.org/") as it does more than just lunix. GL :)

I use it for Win7 and Ubuntu. :)

---

### Post by wilee-nilee on 2011-04-19
> **claven123 said:**
> Clonezilla sounds like a good option.  Are there wiki's or how to's on doing this.  I seen some by googling, but some seem old.   And they don't seem to deal with the dual boot issue of windows and linux.

So, I'll dig a bit more....

I have an older smaller HD, but I'm not sure it will work.  I'll opt to upgrade this HD.

Thanks,

D

You can clone the whole HD, or individual partitions, windows or linux, and many other partition types. It will save the data to a external hd all in the same partition in a folder, as data, individually named per HD or partition, you name them.

---

### Post by claven123 on 2011-04-19
So, I buy a 1TB HD and I can use clonzilla to make a complete copy of my HD and then place that on my new 1TB HD.  Then it will be just as if I never changed to a new HD, except the larger size.  

I would assume I would need to adjust the partitions for windows and linux to accommodate the larger drive.

D

---

### Post by Learning Linux 2011 on 2011-04-20
> **claven123 said:**
> So, I buy a 1TB HD and I can use clonzilla to make a complete copy of my HD and then place that on my new 1TB HD.  Then it will be just as if I never changed to a new HD, except the larger size.  

I would assume I would need to adjust the partitions for windows and linux to accommodate the larger drive.

D

Basically that is it, yes. 

You don't necessarily *have* to adjust your partitions, but you can if you wish.  

Then that 1TB hard drive would be your new main drive and you can use the old one for data or whatever.


If you want to use Clonezilla, there is some information on their web site ([http://clonezilla.org](http://clonezilla.org)) about how to actually clone disc to disc:
[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

Basically you download an ISO image, burn it to a CD, boot from the CD and then do the cloning.

---

### Post by claven123 on 2011-04-20
Odd, I contacted HP and they said the 1TB is not supported by my computer?  I find that odd.  Ok, well.  I would assume I could buy a 'bare' hard drive and an external case with USB cable and get to making the clone.
 
I really, really appreciate pointing me to that help page, I looked and for some reason missed it!
 
Thanks for all the help!!

---

