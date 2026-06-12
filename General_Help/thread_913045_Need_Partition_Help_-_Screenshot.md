---
title: "Need Partition Help - Screenshot"
date: 2008-09-07
forum: General Help
---

### Post by risknothin on 2008-09-07
I want to partition the hard drive into 2 separate drives but i get this error. What do i need to do?

Thanks

---

### Post by dorkdork777 on 2008-09-07
You can't resize a mounted partition, and you can't unmount your / partition - it's what your system is running from..

Try starting an Ubuntu Live CD or the Gparted Live CD ([found here]("http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=garr&filename=gparted-live-0.3.7-7.iso&78817496")) and running Gparted from that. :)

---

### Post by risknothin on 2008-09-07
so i cannot make a new partition while in ubuntu?

I need to run the gparted cd during boot to do it?

---

### Post by forger on 2008-09-07
Either boot from the gparted cd or from the ubuntu live cd and head to System > Administration > Partition editor

You can't format/resize the "root" / partition while it's being used by the operating system.. that's like formating Windows C:\ (install directory) while in Windows

---

### Post by risknothin on 2008-09-07
ok so i was able to create a second partition but now i am back in ubuntu and dont have permission to use it. can someone help me?

---

### Post by bodhi.zazen on 2008-09-07
permissions and setting them are dependent on the file system :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by lost_soul on 2008-09-07
try opening nautilus in sudo mode .. then go to /home/media right click on ur hard drive then propreties then permissions and try to change the owner to u and enable read and write maybe that will solve the issue

---

