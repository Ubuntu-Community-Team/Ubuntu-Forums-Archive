---
title: "New install comming up :)"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by GQed76 on 2006-02-04
Well Ive decided I no longer need windows.  Soon Ill be wiping my hard drive and placing Breezy on it.

Id like 2 partitions, but id like my home directory on the 2nd incase any disaster hits, my data is still there.

Can anyone point me thru the steps on install ill need to do?

---

### Post by Zelut on 2006-02-04
I've done a setup this way but I should mention that if your /home is on a second partition on the same drive, if the drive fails that partition fails too.  Its usually a better idea to have the /home (or something you want more 'backed-up' to be on a second HDD altogether.

During the partitioner during installation you'll have an option to edit your partitions.  You can first delete all partitions (this is just some basic instruction..), manually edit one to be found at /home (and size it, of course) and then 'automagically partition remaining' (or whatever the option is).  That'll create your / & /swap and you should be done.

If you're looking to put /home on a second hard drive that might be just a tad different but its all in the same place.  You'd have to select the second drive & manually create that into /home and then automagically partition remaining on the other drive... 

hope that made some sense

---

