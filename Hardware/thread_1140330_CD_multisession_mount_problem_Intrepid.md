---
title: "CD multisession mount problem Intrepid"
date: 2009-04-27
forum: Hardware
---

### Post by miousername on 2009-04-27
When I insert a multissession CD nautilus try to mount the media but it spents a lot of time to do it and after 15s a dbus error appears:


DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

This is the output of dmesg:

[ 2393.224833] sr 1:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 2393.224839] end_request: I/O error, dev sr0, sector 1435104
[ 2393.224847] Buffer I/O error on device sr0, logical block 358776

I tried to start ubuntu in recovery mode and from a shell i could mount cd with any problem.
I tried also to remove from fstab the line:


/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

because I wanted to mount manually the drive but nautilus tried to mount the CD with the same problem...
So, do you know a solution??
How can I stop automatic nautilus CD\DVD mount ??

Thx for all your suggestion!:(

---

### Post by logos34 on 2009-04-27
> **miousername said:**
> 
How can I stop automatic nautilus CD\DVD mount ??

nautilus>edit>prefs>media tab>UNCHECK "Browse media when inserted" option

---

