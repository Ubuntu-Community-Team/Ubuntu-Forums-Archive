---
title: "1 iscsi array, mounted on multiple guests?"
date: 2008-10-27
forum: Hardware
---

### Post by NaughtyusMaximus on 2008-10-27
I'm new to the world of iSCSI and need a bit of help.  I have a shiny new Promise VTrak M210i iSCSI enclosure, with two LUNs.  On one of the LUNs I will be placing VM images, and on the other email server data (Zimbra).

I would like to have both of the LUNs mounted on two different machines.  Is that possible just with iSCSI alone, or do I need to set up another machine to mount, and then share (via NFS or Samba) to the two other boxes?
[B]
Is this possible:[/B]
Server 1:
/mnt/vm -> iSCSI LUN 0
/mnt/zimbra -> iSCSI LUN 1

Server 2:
/mnt/vm -> iSCSI LUN 0
/mnt/zimbra -> iSCSI LUN 1

**Or do I have to do this:**
Server A:
/mnt/vm -> iSCSI LUN 0
/mnt/zimbra -> iSCSI LUN 1

Server 1:
/mnt/vm -> Server A NFS Share
/mnt/zimbra -> Server A NFS Share

Server 2:
/mnt/vm -> Server A NFS Share
/mnt/zimbra -> Server A NFS Share

---

### Post by NaughtyusMaximus on 2008-10-28
Any thoughts?

---

