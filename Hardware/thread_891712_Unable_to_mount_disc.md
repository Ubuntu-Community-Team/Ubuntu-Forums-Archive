---
title: "Unable to mount disc"
date: 2008-08-16
forum: Hardware
---

### Post by blackriven on 2008-08-16
I dual boot Ubuntu 8.04 with Vista on a partitioned drive. When I try to access the Vista partition from Ubuntu it says that it's unable to mount the drive and adds this in the details: 

$LogFile indicates an unclean shutdown (0,0) failed to mount '/dev/sdal': Option not supported Mount is denied because NTFS is marked to be in use. Possible options:.........

It then however attempts to mount it, and after a while gives the following error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

The computer is an HP Pavilion dv6500

---

### Post by wilbbe01 on 2008-08-16
Did you try booting into windows and telling it to shutdown.  Unclean shutdown generally means the machine went down hard, as in a power outage or someone intentionally cutting the power.  I would boot into windows, then shutdown, then try mounting it in ubuntu again.

---

