---
title: "[SOLVED] gparted help with partitions"
date: 2008-08-17
forum: General Help
---

### Post by PGScooter on 2008-08-17
Hi, I am having trouble resizing partitions. Attached is a screen shot from gparted (boot cd). I would like to add more space to my windows ntfs partition- /dev/hda1 and my swap partition-/dev/hda6 , and take away from my ubuntu partition- /dev/hda5 . I could not figure out how to do this. GParted let me reduce the ubuntu partition (this is shown in the picture, although I did not go through with it). It also let me increase my swap. But it would not let me enlarge my windows partition.

How can I enlarge /dev/hda5 without reinstalling everything?

note: I still have my data, although backed up, on both the windows and ubuntu partitions.

Thank you.

---

### Post by Elfy on 2008-08-17
To be able to resize hda1 you need to shrink hda2 (the extended) then the free space should be outside the extended partition and available for hda1 to grow.

> How can I enlarge /dev/hda5 without reinstalling everything?Is this a typo - I thought you wanted to shrink hda5.

---

### Post by PGScooter on 2008-08-17
> **forestpixie said:**
> To be able to resize hda1 you need to shrink hda2 (the extended) then the free space should be outside the extended partition and available for hda1 to grow.

Is this a typo - I thought you wanted to shrink hda5.

Yes, you are right, I do want to shrink hda5. ok, I'll mess around in GParted some more. I remember reading in various places that shrinking a partition from the beginning is not a good idea. Should I be worried about shrinking hda5 like that then?

thank you

---

### Post by Elfy on 2008-08-17
Well - you can either shrink from the beginning or the back but if you do that then everything has to be moved as well.

I have successfully shrunk from the beginning, I think that previously you couldn't do it with gparted, although I stopped using gparted when I had a dodgy version (I think).

> Should I be worried ...I always worry until it's finished, but one way or the other you have to get the unallocated space at the front contiguops with hda1.


Whatever way you do it - it is likely to take quite some time to do it -

---

### Post by PGScooter on 2008-08-17
OK, well I guess I'll just give it a shot since I have my data backed up. thanks

---

