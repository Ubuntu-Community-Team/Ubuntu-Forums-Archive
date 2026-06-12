---
title: "a question on adding swap space"
date: 2008-10-10
forum: General Help
---

### Post by huangweiqiu on 2008-10-10
When I installed Ubuntu8.10 ,I forgot to format a swap partition. Now I have take some space from C: and format it to swap,but I don't know how to add the swap partition to the Ubuntu 8.10.
help please thanks in advance!

---

### Post by iaculallad on 2008-10-10
Try reading this [SWAP Partition FAQ]("https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0") from Ubuntu Community.

---

### Post by Yellow Pasque on 2008-10-10
I'm not sure if I agree with the way the document adds it to /etc/fstab. If you already have the swap partition, then run the following command to get your UUID:
```
$ blkid
/dev/sda1: UUID="7a119114-4fd7-4ee0-922f-a7d03a5b4b3e" TYPE="ext3" 
/dev/sdb2: UUID="0302e2bf-cf4c-43fb-8deb-21a120eb723e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="0fa7190f-c87d-4d39-b960-52e66566a1e8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: **TYPE="swap"** UUID="**196c7c15-ca90-492f-a140-1957cfb65bfe**"
```
Open /etc/fstab for editing:
```
gksudo gedit /etc/fstab
```
Add the line:
```
UUID=<string from blkid command>   none   swap   sw   0   0
```
Save and quit. Swap will be auto-mounted on subsequent boots.

---

