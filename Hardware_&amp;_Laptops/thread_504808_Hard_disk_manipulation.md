---
title: "Hard disk manipulation"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by YigalB on 2007-07-19
I have two hard disks  (say hdisk1 and hdisk2) inside my PC.
In the past, I installed Edubuntu on both, one at a time, while the other was disconnected. During boot I can chose which one to boot from.

Now I want to erase all the content in the hdisk2, boot only from hdisk1, and have all free space  avilable for all programs, regardless on which disk the data will reside on.

What steps should i do to meet that goal?

---

### Post by brettr on 2007-07-19
One way would be to install gparted, partitioning program and erase disc2. You will probably also want to update  your grub boot menu. And you will also probably have to edit /etc/fstab in order to get disc2 mounted where you want it. That should give you an idea of what needs to be done. As for details on doing each thing, search around the forums, there should be information about each process.

---

