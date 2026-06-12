---
title: "Connecting to an iSCSI connection"
date: 2011-03-24
forum: Hardware
---

### Post by CheezItMan on 2011-03-24
My Windows Server System admin setup an iSCSI share for me, but I can't seem to connect to it.  

 [http://ubuntuforums.org/attachment.php?attachmentid=186938&stc=1&d=1300943218]("http://ubuntuforums.org/attachment.php?attachmentid=186938&stc=1&d=1300943218")

[http://ubuntuforums.org/attachment.php?attachmentid=186939&stc=1&d=1300943218]("http://ubuntuforums.org/attachment.php?attachmentid=186939&stc=1&d=1300943218")
 
[http://ubuntuforums.org/attachment.php?attachmentid=186940&stc=1&d=1300943218]("http://ubuntuforums.org/attachment.php?attachmentid=186940&stc=1&d=1300943218")

[http://ubuntuforums.org/attachment.php?attachmentid=186941&stc=1&d=1300943218]("http://ubuntuforums.org/attachment.php?attachmentid=186941&stc=1&d=1300943218")


I set it up following this [tutorial]("http://www.cyberciti.biz/faq/howto-setup-debian-ubuntu-linux-iscsi-initiator/"), but it's not working...



root@www2:~# /etc/init.d/open-iscsi restart
 * Disconnecting iSCSI targets
   ...done.
 * Stopping iSCSI initiator service
   ...done.
 * Starting iSCSI initiator service iscsid
   ...done.
 * Setting up iSCSI targets
iscsiadm: Could not login to [iface: default, target: iqn.1991-05.com.microsoft:pd2-pd2-video-target, portal: 192.168.150.3,3260]: 
iscsiadm: initiator reported error (8 - connection timed out)
iscsiadm: Could not log into all portals. Err 8.
   ...done.

---

