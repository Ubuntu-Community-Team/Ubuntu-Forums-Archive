---
title: "Combining two hdds into one /home"
date: 2009-06-25
forum: Hardware
---

### Post by zagabar on 2009-06-25
Hi there.

I have a server with ubuntu installed on one 80gb hdd. The space on the partition mounted as / is starting to run out becase users  uploads stuff in their home dirs with ftp. I connected a second 80gb hdd to the computer and I would like it to exted the space on /home. How can I do this in a nice way? It it possible to do without using a RAID or LVM method that causes the files to be destroyed?

---

### Post by ronparent on 2009-06-28
Depends on how handy you are with command line operations. It is possible to transparently relocate users to the new drive by moving their /home partions there to a single or separate partitions. Check out this reference: **[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)**

---

