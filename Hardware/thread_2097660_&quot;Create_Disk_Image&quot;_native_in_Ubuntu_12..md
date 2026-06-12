---
title: "&quot;Create Disk Image&quot; native in Ubuntu 12.04"
date: 2012-12-24
forum: Hardware
---

### Post by RogerDavis on 2012-12-24
Where can I find a detailed explanation of the "disk image" function found in ubuntu 12.04:

Applications > Accessories > Disks > Click gear symbol to get "Create Disk Image" as a choice?

I need to know how to use it, and other details.

This is NOT an application installed separately, it is PART OF Ubuntu.

---

### Post by cwsnyder on 2012-12-24
Open a terminal and type **man genisoimage**, then when you are finished reading type **man growisoimage**.

---

### Post by RogerDavis on 2012-12-24
So it appears that this will only work with CD or DVD disks, not to clone to a second hard drive?

---

### Post by cwsnyder on 2012-12-24
To clone a hard drive, use either Clonezilla or the command line dd.

---

