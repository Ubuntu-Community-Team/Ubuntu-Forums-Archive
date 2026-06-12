---
title: "Unbable to mount [ cd rom name] w"
date: 2009-05-15
forum: Hardware
---

### Post by MadMax2 on 2009-05-15
Using 8:10 Intrepid for a few weeks but this problem has just appeared:
I tried to read to data CD's and got the following message:

Unable to mount J and K w
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.

 Possible causes include: 
-the remote application did not send a reply
-the message bus security policy blocked the reply
-the reply timeout expired
- or the network connection was broken.

I tried a different CD data disk left it in and did a restart. The icon was on the desktop and it displayed.
Tried the original and it said:
Unable to Mount Volume 'J and K w'
 Mount: block device /dev/scd0 is write protected, mounting read only mount: No medium found.

 Permissions changed?
john@LoungePC:~$ ls -l /media

total 2

lrwxrwxrwx 1 root root    6 2009-04-17 19:22 cdrom -> cdrom0

dr-xr-xr-x 1 root root 2048 2006-03-13 13:30 cdrom0

john@LoungePC:~$

---

