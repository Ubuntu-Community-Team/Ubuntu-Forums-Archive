---
title: "No guided - use largest continuous free space"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by MarcusA on 2009-03-05
Hello,

I shrank my volume in Vista to use for Ubuntu 8.10, but when trying to install Ubuntu I don't have the "guided - use largest continuous free space" option during installation. I get Use entire disk and manual. Any help on this please? 

sorry for my English..

---

### Post by linuxuser21 on 2009-03-05
> **MarcusA said:**
> Hello,

I shrank my volume in Vista to use for Ubuntu 8.10, but when trying to install Ubuntu I don't have the "guided - use largest continuous free space" option during installation. I get Use entire disk and manual. Any help on this please?

Ubuntu can shrink a volume under the 'manual' option.

---

### Post by MarcusA on 2009-03-05
I heard the manual option is not for n00bs though haha. :D I'm pretty new to this. Do I have to increase the volume in Vista back and go with manual then?

---

### Post by MarcusA on 2009-03-05
Or if someone can show me a guide on what buttons to click in the "manual" option? I can't find what I'm supposed to do in manual exactely..

---

### Post by Mark Phelps on 2009-03-05
> **linuxuser21 said:**
> Ubuntu can shrink a volume under the 'manual' option.

Yeah, it "can" but sometimes, when it does that, it leaves Vista in a state where it won't boot properly.  When that happens, you have to boot from a Vista DVD, or a Recovery CD, and run Vista Startup Repair; otherwise, Vista will remain permanently unbootable.

So, unless you have a Vista DVD or a Recovery CD lying around, it's not a good idea to use anything other than Vista to shrink a Vista OS partition.

If the partition has already been shrunk (as the OP indicated), and there is free space now on the drive, it's not a shrinkage problem -- it's a problem with the Ubuntu installer not seeing the available space.

I would suggest booting into the LiveCD and using the Partition Editor to format the free space as Ext3. Upon reboot and install, the Ubuntu installer should now see the partition.

---

### Post by ooofence on 2009-03-05
I had the same issue when I first shrank Vista.  I believe it happens because even though you shrank Vista and created a new partition, it still shows up as allocated (Volume).

What I did was to go to Disk Management (Control Panel -> Administrative tools -> Computer Management -> Storage -> Disk Management)in Vista, and remove the volume of the partition you want to install Ubuntu on, then when you go to install Ubuntu, you will get the option you are looking for.  Hope this helps

---

### Post by MarcusA on 2009-03-05
Thanx people, I now have ubuntu installed! :)

---

### Post by lindsay7 on 2009-03-05
+1 did the same.  I what did to cause confusion with the Ubuntu installer was to back out of the install after it looked at setting up the partitions, it gives you a worning, but it is not very clear on what it will do. When I went back in to do the install it would not see the existing windows partition. I did what you did but I just etended the windows partition back to the whole disk.

---

