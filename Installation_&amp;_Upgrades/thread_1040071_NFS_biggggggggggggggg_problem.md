---
title: "NFS biggggggggggggggg problem"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by tigga on 2009-01-15
Hello ,
I have 2 virtual machines on ubuntu created by VMware.
The firt is windows XP and the other is debian etch.

The problem is ,
I want to create NFS partition and i want that the three machines(ubuntu,XP,debian) to be able to acces to this partition.

can anyone help me

---

### Post by ubhi on 2009-01-15
if NFS is Big problem, then i think you can use samba share as well... for file sharing... because its bettar to use samba for linux and windows enviornment...

---

### Post by stefangr1 on 2009-01-15
I have a similar setup, and it is really easy for the linux machines. On the server you do:
sudo apt-get install nfs-kernel-server nfs-common
and on the clients:
sudo apt-get install nfs-common

next you have to configure your router or dhcp server such that your virtual machines get fixed ip-addresses (for security reasons)

then you have to edit your /etc/exports

for each vm you add one rule like:
/files 192.168.#.# (rw,no_root_squash,async)

and do sudo exportfs -a to make nfs use the new configuration.

After that you can mount the nfs manually, or add an entry to your fstabs.

You can allow entire subnets or the whole world access, but that's not such a good idea. If the vm's are on their own host only subnet, btw., you could easily give that subnet access off cause.

---

### Post by meindian523 on 2009-01-15
Please use meaningful titles for your threads.For this case,you could have used "NFS share between VM Debian Etch,XP and Ubuntu"

---

