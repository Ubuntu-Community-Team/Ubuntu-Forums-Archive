---
title: "Swapping DVD Drive"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Emerzen on 2007-05-09
Here's my dilemma:

I have a DVD ROM drive installed that works w/o a hitch in Feisty.  I recently purchased a replacement DVD burner.  I would like to install the Drive w/o having to reinstall Feisty and all the configurating I've done.

Question: can I simply pull out the old drive and insert the new one or will I have to reconfigure Feisty, fstab for example???

---

### Post by dfreer on 2007-05-09
should be able to just replace the old drive with the new one. make sure the jumper setting is the same (master - master, slave - slave, cable select - cable select). fstab for cd drives really only has to deal with the device location, and that shouldn't change if you put the new DVD drive where the old one was. Even if you left the old one in there alongside the new one ubuntu should see both drives, you *may* just need to add the new drive once to fstab.

---

### Post by Emerzen on 2007-05-09
Hey, thanks, I'm going to give it a whirl.

---

### Post by Emerzen on 2007-05-10
Went off w/o a hitch for anyone else who make wonder about it.

---

