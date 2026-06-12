---
title: "Iscsi connection"
date: 2015-11-21
forum: Hardware
---

### Post by gabor5 on 2015-11-21
I have a problem with my ISCSI storage, and hop you can help me to  solve this problem. The system was made following this tutorial: 
  [https://help.ubuntu.com/community/HighlyAvailableiSCSITarget](https://help.ubuntu.com/community/HighlyAvailableiSCSITarget)
  So i have two nodes, 1-1 NIC for DRBD replication, ietd to connect the storage and heartbeat to keep them in sync.
  Everything works fine, a tested it with restarting heartbeat as  written in the last point. i was watching /proc/net/ietd/session, and  the change is OK, the session builds up very quick. The problem comes when i restart the passive node . The connection to  the storage still works, but if i restart heartbeat again to give  control to the system i have rebooted i have to wait for ietd for about  20-30 sec. in this period the sessions build up, and the connection  works again but very slow. After this first change will the change fast again untill i reboot one  node... I made logs when i restarted heartbeat after boot and one of the  heartbeat restart after. I was looking for differences in these logs  but found nothing. Do you have any idea why the session build up so slow  in the first heartbeat restart?
  thanks for your help

---

### Post by gabor5 on 2015-11-24
So, i have found something in tshark. In normal case, if i restart heartbeat i see the login - login succesful messages in the iscsi communication in 2-3 sec. If i reboot the the node and try to restart heartbeat it takes more than 20 (!) sec to start iscsi login communication.

---

