---
title: "[SOLVED] Installing ubuntu on another partition."
date: 2008-07-27
forum: General Help
---

### Post by LowMen on 2008-07-27
I have been searching for an answer on this, some advice I followed and may have zigged instead of zagged.

I am setting up a second machine that has XP on it already, I used partition magic to create a ext 3 partition, loaded the Ubunto 8.04 edition.  I get to a screen "prepare disk space" with 3 options:

1/ guided - resize SCS15 (0.0.0), partition #1 (sda) and use freed space.  {also has new partition size with 9% cannot read the rest and Ubuntu 8.04.1 91% (120.7 GB)

I chose this option above and get box about new partition size, and prev changes have to be written to disk.  I choose cont and get to small too size.  

Hope this is enough info to help.

---

### Post by mikewhatever on 2008-07-27
You should also have an option of manually editing partition table. That's the way to go. It's also possible to delete the partition you prepared for Ubuntu and go with use the free space. This one is easier cause it should also take care of creating the swap partition.

---

### Post by Elfy on 2008-07-27
If you have made the partition ready to install to then edit the partition with the partition editor - in sys admin menu.

You need a couple of partitions at the minimum - one for / and one as swap

Open the editor - resixe the partition you have already made so that there is 1.5xRAM unallocated - format that new small partition as swap. Apply changes and close when finished.

Restart the installation - at partition options choose manual

Select the ext3 partition and click edit - near bottom of screen - in new window select a mountpoint of /

Close - it will go back to first screen , enable it to format the partition. Continue with installation - swap will be recogniosed and used without intervention.

---

### Post by LowMen on 2008-07-27
I would like to thank you both for the advice.  I ended up following Forestpixie' advice since I already had the partition created and now have both XP and Ubuntu loaded.  But I seem to have a few boot options now, figure that is normal.  But will look into that later.  :KS

---

### Post by LowMen on 2008-07-27
> **forestpixie said:**
> If you have made the partition ready to install to then edit the partition with the partition editor - in sys admin menu.

You need a couple of partitions at the minimum - one for / and one as swap

Open the editor - resixe the partition you have already made so that there is 1.5xRAM unallocated - format that new small partition as swap. Apply changes and close when finished.

Restart the installation - at partition options choose manual

Select the ext3 partition and click edit - near bottom of screen - in new window select a mountpoint of /

Close - it will go back to first screen , enable it to format the partition. Continue with installation - swap will be recogniosed and used without intervention.

Sorry forestpixie I seemed to have removed your thanks, but thank you :)

---

### Post by Elfy on 2008-07-28
welcome - can you mark thread solved please

---

