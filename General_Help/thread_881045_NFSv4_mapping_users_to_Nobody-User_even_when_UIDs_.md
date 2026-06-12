---
title: "NFSv4 mapping users to Nobody-User even when UIDs in sync"
date: 2008-08-05
forum: General Help
---

### Post by danfluidmind on 2008-08-05
Hi all. I've set up an NFSv4 export on a SuSE 10 box that I'm mounting on an Ubuntu 8.04 box. This share contains the mysql and postgresql data directories. On the the SuSE side I have the same UIDs in /etc/passwd for the mysql and postgres users as I have on the Ubuntu side (107 and 106, respectively). Yet, when I mount the volume on Ubuntu, idmapd maps them to the Nobody-User user ("nobody" in this case). The users IDs match, but it's still mapping them to nobody.

I've added the line to modprobe nfsd suggested in this bug ([https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/235930](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/235930)), but it still doesn't work.

Can anyone shed some light on how I can get Ubuntu to see that the folders on that share are owned by the mysql and postgres users?

Server /etc/exports:
/exports              *(fsid=0,rw,nohide,sync,insecure,no_subtree_check)
/exports/Databases    *(rw,nohide,sync,insecure,no_subtree_check)

Client fstab:
192.168.100.1:/Databases /mnt/Databases     nfs4     proto=tcp,rw,acl,hard,intr,rsize=8192,wsize=8192  0  0


Thanks
--Dan

---

### Post by danfluidmind on 2008-08-06
Problem solved. The above mentioned bug patch did, in fact, fix the problem. Turned out that I ALSO had a typo in the "domain" line of /etc/idmapd.conf which prevented idmapd from mapping the users.

For future reference, make sure your "domain" lines in /etc/idmapd.conf match on both your NFSv4 server and the client trying to connect to it.

All is good.

---

