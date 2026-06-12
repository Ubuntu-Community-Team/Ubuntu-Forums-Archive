---
title: "How to Reinstall on same partition"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by GZ Expat on 2008-12-17
I installed 8.10 via the quick install in which I created a 10G partition with Windows.  The install went well, but the subsequent update went poorly and my current install of Ubuntu won't remember anything.  The quick install did not give me a /home directory, only a / folder and a swap partition.  

How do I reinstall using the same 10G partition...I am completely stumped as to how to get it installed and then create a /home partition within that 10G partition.

---

### Post by Sam Lars on 2008-12-17
So are you wanting /home to be on a separate partition?
I would boot to the live CD and use the Partition Editor to make your partitions, and when you install you should be able to tell it which one you want for / and which one you want for /home.

---

### Post by GZ Expat on 2008-12-17
My concern is, when I go to the partition editor, it shows me the previous partition for the current install of Ubuntu and then asks for another partition for the current install.  When I switch to manual, I'm not entirely sure the partition I have selected will be the one that the installation will fall on.  At the bottom of the final confirmation page, it does say that the partition I selected would be formatted...but it doesn't say exactly where Ubuntu will be loaded...am I to assume it is being loaded on the partitions that are being formatted?

---

### Post by Sam Lars on 2008-12-17
Yes, it should only format the partition you select for it to be installed on.
You can tell it to mount other partitions as /home and so on, but those will not be touched.

---

