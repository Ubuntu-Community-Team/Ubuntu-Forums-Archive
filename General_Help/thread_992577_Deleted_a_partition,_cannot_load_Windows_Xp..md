---
title: "Deleted a partition, cannot load Windows Xp."
date: 2008-11-24
forum: General Help
---

### Post by slims20 on 2008-11-24
K I made a couple bonehead moves.

First, I installed windows XP and made a smaller partition for backup purposes along with it.  I somehow installed XP fully to both partitions and everytime I load up my computer it asks me which Windows XP I want to start.  

Annoyed by this, I decide to delete the smaller partition.  I put in my XP disk and used it to delete the partition, leaving my primary partition intact.  However, the backup partition was the c:\ and it was the first one on the list, and this is the one I deleted.  

Now the d:\ is still on the list of partitions and it is second on the list under the unpartitioned space.  My computer will not boot it though.  

I can access it via recovery console but I'm a novice with this stuff so help would be appreciated!

Thanks guys.

---

### Post by Bucky Ball on 2008-11-24
Has this post got anything to do with Ubuntu or Linux?

Anyway, I would start again, delete all partitions before you install XP, make one partition for it. Make the other partitions once you're up using 'Disk Management'.

---

### Post by slims20 on 2008-11-24
Oh I'm sorry, I probably shouldn't have posted this on this forum, I didn't realize.

If you guys want to help still it's appreciated. My bad.

Also, I'd rather just be able to boot up the other partition rather than deleting it and starting over.

---

### Post by Bucky Ball on 2008-11-24
Sorry, don't remember how to do this in Windoze. :( Good luck, someone else might pop up. You could have a look around on the net for 'Fix MBR'. I believe there is a thing called 'Fixboot' which runs off the Windoze recovery also, that could do the trick. Have a search on this forum for that. Your problem is not uncommon, but usually some stuff up in an attempted dual boot with a Linux OS. Funny thing is, I had a similar thing happen when I was installing Ubuntu once, Windoze wound up on drive D, and worked fine! lol

But I only had the one install. I think ripping the other install off has somehow stuffed things. A wild guess is that the MBR that was running the show may have been on there. But with Windoze, I am only guessing at this point.

---

### Post by slims20 on 2008-11-25
Thanks for the help, Bucky.  I tried the fixmbr command, and it seemed to do something but I still got the same error.  I then used the fixboot command but got the following message:

"FIXBOOT cannot find the system drive, or the drive specified is not valid".

I'll keep searching the web for answers.

---

