---
title: "NTFS in LVM system"
date: 2012-10-22
forum: Hardware
---

### Post by Chris_huh on 2012-10-22
Evening...

Can you set up NTFS partitions in an LVM?

I currently have 2x3TB blank hard disks that I want to set up in ubuntu. It's going to be for a HTPC so i want them to be seen as one drive. I originally thought of setting them up in a RAID, but i want to be able to add to them as i go, so as i gather it, RAID won't be suitable. 

Then I stumbled across LVM. Am i understanding correctly that LVM essentially allows you to group together previously formatted partitions in such a way that the OS sees it as just one large partition? And that you can add extra partitions, no matter what size they are, as you want, without any affect on the current data?

At least, that's how i understand it. 

Anyway, i have formatted the HDDs as NTFS but in Logical Volume Management i can only see the system SSD and an external FAT32 drive. Are NTFS not supported in lvm??

thanks guys

---

### Post by Chris_huh on 2012-10-22
Ah, well i've been able to add the two NTFS partitions to a volume which is now seen as 6TB, but i had to format it. Perhaps that is how it works, but i was imagining you wouldn't need to reformat the partitions. 

I was hoping there would be a way you could split the volume up into it's constituent partitions at a later date and still access all the data on the individual partitions. Or was i misunderstanding LVM?

---

### Post by oldfred on 2012-10-22
I have not used LVM. But have a couple of links.

Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

### Post by Chris_huh on 2012-10-27
Thanks Fred. that's given me a bit of a better idea of what LVM is. I'm still a little unclear on one thing:

Can I take out a partition from the LVM while keeping the data on that partition? Eg If i have an LVM with a 1 and 2 TB system, can i just remove the 1 TB drive from the LVM with all my files still on it? 
I think I would only ever use this if i wanted to move from ubuntu to windows and decided to break the LVM, leaving the two partitions as just that, partitions, for windows to see.

thanks

---

### Post by oldfred on 2012-10-27
My understanding of LVM is if one drive breaks or fails then you have lost all your data not just part. So if you want to undo an LVM you have to shrink it first into one drive or backup fully first.

Unless running Windows, I cannot really suggest NTFS. With Ubuntu, it will run fsck every so many reboots but cannot schedule chkdsk on NTFS partitions. Also You have to have a Windows install or repairCD or USB to run the chkdsk on the NTFS partition. And that should be done periodically, Windows does not schedule it.

---

