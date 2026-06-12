---
title: "Dual Boot -&gt; Reinstall Ubuntu"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by Alexandre Charoy on 2009-09-12
Hi!

I'm aware that many threads and documentation files already threat this topic, but I have some questions left - I'm not used to partitioning etc. and it "scares" me...

Situation: I have Windows Vista and Ubuntu 8.10 as a dual boot. My Ubuntu is totally broken after I shut down my computer during the upgrade from 8.04 to 8.10 (it was a mistake of course :(). After deleting all broken packages and doing some things I didn't understand, I didn't even have a GUI left... I managed to reinstall ubuntu-desktop, but many packages are gone, and I can only start a "low graphics mode" or something similar.... Now I would like to re-install Ubuntu.

Questions:
Can I install the latest Ubuntu distro on the same partition Ubuntu is already installed?
Do I need to format the partition first, or does the installtion process format the partition?
If I need to format, can I just format the partition from Windows, and then install Ubuntu on it with the installation CD?
Or do I need to delete the partition and give the space back to my windows partition and then install Ubuntu and create a new partition for it during installation?

Thanks for your help and time!

---

### Post by Partyboi2 on 2009-09-12
>  Can I install the latest Ubuntu distro on the same partition Ubuntu is already installed?

First check what partition your / is on before reinstalling by opening a terminal (Applications>Accessories>Terminal) and using
```
df -h
``` this will tell you what partition your / is, eg /dev/sda3
Then when you reinstall choose the "Manual Partitioning" option at the partitioning stage. Then  choose to edit you old ext3 / partition. (/dev/sda?)  and reset the mount point to / and tick the box to format.
This will reuse the same / partition but will format and install Ubuntu again.

---

### Post by Alexandre Charoy on 2009-09-13
Ok I got it, Ubuntu 9.04 is up :)
Thanks!

---

### Post by raoshivani on 2012-05-18
I really like this thread, but what happens to the MBR and grub? is it not stored on /?

and also if i just format and choose that partition to install ubuntu, /home stays intact?

---

### Post by darkod on 2012-05-18
> **raoshivani said:**
> I really like this thread, but what happens to the MBR and grub? is it not stored on /?

and also if i just format and choose that partition to install ubuntu, /home stays intact?

No, grub2 should go to the MBR of the disk, not on the root partition.

If you have separate /home partition you need to tell the installer to use it during the install. In the manual partitioning, click the partition and select Change, then choose the filesystem in the Use As field, for example ext4 if it's ext4. Select mount point /home, that will use it as /home. Make sure the format box IS NOT selected, otherwise you will lose the data.

---

### Post by oldos2er on 2012-05-18
Old thread closed. 

raoshivani, if you still have questions, please start a new thread.

---

