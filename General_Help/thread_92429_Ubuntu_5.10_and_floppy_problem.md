---
title: "Ubuntu 5.10 and floppy problem"
date: 2005-11-19
forum: General Help
---

### Post by Chris180775 on 2005-11-19
Hi at all,
I have installed Ubuntu 5.10 and then upgraded the pmount package to 0.9.6.1 for the problem related of accessing at the floppy disk.
Now, when I try to access to the floppy the message is:

Unable to mount the selected volume.
Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

Can anyone help me? :confused: 

P.S. Thanks in advance and sorry for my horrible English. :oops:

---

### Post by Chris180775 on 2005-11-19
Opss... I have changed on the file /etc/fstab the filesystem type from "auto" to "msdos" an now magically works!!!

---

