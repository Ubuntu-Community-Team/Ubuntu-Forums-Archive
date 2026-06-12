---
title: "CD multissession mount problem on Intrepid"
date: 2009-04-09
forum: Hardware
---

### Post by miousername on 2009-04-09
When I insert a  multissession CD nautilus try to mount the media but it spents a lot of time to do it and after 15s a dbus error appears:


DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

This is the output of dmesg:

[ 2393.224833] sr 1:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 2393.224839] end_request: I/O error, dev sr0, sector 1435104
[ 2393.224847] Buffer I/O error on device sr0, logical block 358776

I tried to start ubuntu in recovery mode and from a shell i could mount cd with any problem.
I tried also to remove from fstab the line:


/dev/scd0 	/media/cdrom0	udf,iso9660 user,noauto,exec,utf8 	0	0

because I wanted to mount manually the drive but nautilus tried to mount the CD with the same problem...
So, do you know a solution??
How can I stop automatic nautilus CD\DVD mount ??

Thx for all your suggestion!

---

### Post by kpkeerthi on 2009-04-09
```

/dev/scd0 /media/cdrom0 udf,iso9660 **[COLOR="Red"]user[/COLOR]**,noauto,exec,utf8 0 0

```

Removing the 'user' option from the FSTAB mount line should allow only super-users to mount the disc, manually. A reboot is required.

---

### Post by miousername on 2009-04-09
Many thanks for the answer,I've tried but the dmesg is the same:

[  148.083147] sr 1:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  148.083153] end_request: I/O error, dev sr0, sector 1435104
[  148.083162] Buffer I/O error on device sr0, logical block 358776

I've to wait a long time before the media is ready, the time is more long for CD & DVD with a lot of sector errors....

When I tried to mount it in recovery mode (root shell recovery) the problem doesn't appear...
why??

---

### Post by miousername on 2009-04-10
Please help me!do you have other suggestion??

---

