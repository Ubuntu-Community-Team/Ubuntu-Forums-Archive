---
title: "/home partition got separated after reinstalling..."
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-05-25
manual partition before reinstallation of Ubuntu 8.10..
1 GB-swap
12 GB-mount point (/)
12 GB-(/home)
after first installation my files stored in /home....

during reinstallation 
i selected (/) partition alone n formatted it..
rest of the partition was in "do not use partition" option..

now my previous home partition is available as separate drive as my other windows partition...

how to merge it to the /home as i had before?
can someone explain why it happended?
does that separate 12 GB partition affect any application installation,internet speed?

---

### Post by Hobgoblin on 2009-05-25
When you reinstalled you should have done a manual partitioning and selected the previous /home partition, assigned it to /home and made sure the "format" tickbox was not checked.

---

### Post by vpnm_87 on 2009-05-25
thanks for the advice...ll try that in future...
any way to fix it now..
is this advantageous or gonna cause trouble in future?
should i better reinstall ubuntu again?

---

### Post by logos34 on 2009-05-25
take a look at[ this guide]("http://www.psychocats.net/ubuntu/separatehome") to moving /home to separate partition. Except in this case all you really need to do is boot the live cd, delete /home dir on the root partition and make a new one in its place, then edit fstab so the system mounts your separate /home partition (sda3?) at /home dir.  Understand?

---

### Post by vpnm_87 on 2009-05-25
understood:-)thanks for directin me to that excellent guide:-)
but the introduction part itself says its better to have the /home separately(if i hav understood properly):-)
so shall i better leave it as it is or move the separate partition into 
root(/)?
kindly provide some advice:-)

---

### Post by Hobgoblin on 2009-05-25
Yes, it can be advantageous to have /home on a separate partition. 

You need to leave / where it is and change your /etc/fstab to mount /home to your old /home partition (after deleting the current home folders).

---

