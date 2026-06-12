---
title: "External USB HD, Partitioning for clean instal"
date: 2010-05-18
forum: Hardware
---

### Post by colintivy on 2010-05-18
I have an 80GB HD in an enclosure and wish to format it for either a clean install of Lucid for trial use or a complete BU of my existing Hardy in an elderly laptop with the clean install on the normal HD. To my surprise when I formatted the drive to ext3 (as I thought) from the complete Windows 98SE system that was upon it, Ubuntu mounts it but has divided it into 3 equal partitions which look like separate drives. Two are etc3 but the 3rd is still a Windows format but with nothing in it. I thought that I would have just one drive just with etc3. Is this due to an accessing problem? What advice is there to sort this out if indeed this is inappropriate?

On the assumption that I do manage this, what advice is there on my two alternative plans.. I am very loath to lose my working Hardy until Lucid is shown to work OK. I intend to await the arrival of a DVD with Lucid from Linux Format to allow me the luxury of a clean install, as I did with Hardy which went flawlessly. The evidence from forums seems that this could be unlikely and I do not want to be unable get online via Hardy to get help.

I have copied my /home onto a 16GB USB Stick, ready for its own partition, and see that it is only holding my own documents. I note that, in fact, /home has three parts, the first lists my apps, the second my documents and the third a lot of administrative files and logs etc., Are all three required for putting on the new distro (if successful) from the Back-up on the stick?

All help welcomed!

colintivy :confused:

---

### Post by spydeyrch on 2010-05-18
As far as the partition issues go, have you tried GParted? I would use GParted to change/delete/create the partitions as you see fit/need. It is a pretty simple program to use.

-Spydey :guitar:

---

### Post by colintivy on 2010-05-19
Thanks spydey!

Yes I know a bit about GParted but was more interested in why my Ext.HD got itself split into 3 separate drives (sdb1,2 & 3) in the first place. I got there by mkfs.ext3 from an apparently single drive.

I was also interested in the practical procedures to achieve my deired aim of having a working 10.04 for evaluation while maintaining a working 8.04 without going to a dual boot. I do not intend to run 10.04 with any other OS oce I am satisfied it does everything that Hardy does satisfactorily now.

I am a bit reluctant in diving straight in having read so many posts from others who have suffered pretty fundamental snags post 9.10 and earlier upgrades and installs.

colintivy

---

