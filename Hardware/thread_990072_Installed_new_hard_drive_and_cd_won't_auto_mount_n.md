---
title: "Installed new hard drive and cd won't auto mount now"
date: 2008-11-22
forum: Hardware
---

### Post by AdamGott on 2008-11-22
Quick summary:

Ubuntu 8.10. 

I got a new 1TB drive for media storage, It is PATA.  I replaced my SATA 500 gig drive with this one and it changed all of my hard drive 'lettering' - i.e. /dev/sdb became /dev/sda and so on.  It took me a while but I got my Ubuntu reconfigured correctly (I think) but for some reason I can't get my cd-rom to auto mount when I insert a disc.  It was working before so I assume it is related to my hard drive swapping.

here is my line from fstab:
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

The media will mount when I do it manually but instead of pulling the volume label it now mounts as cdrom0.

I have searched and searched for a solution but I can't find it. 

Thanks.

---

### Post by taurus on 2008-11-22
Look at the messages log to see what is the name of your cdrom.  Could be something like /dev/sdc1 or something like that.  Try changing the /dev/cdrom in /etc/fstab to that and reboot.  Now, is it mounted when you insert a disc?

```
sudo more /var/log/messages
```
Tab the Space bar for the next 24 lines.

---

### Post by AdamGott on 2008-11-22
I get this - 

```
Nov 22 07:56:08 adam-desktop kernel: [80836.192426] type=1503 audit(1227365768.6
02:13): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsui
d=7 name="/var/run/samba/gencache.tdb" pid=20985 profile="/usr/sbin/cupsd"
Nov 22 07:56:08 adam-desktop kernel: [80836.195700] type=1503 audit(1227365768.6
02:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsui
d=7 name="/var/run/samba/gencache.tdb" pid=20985 profile="/usr/sbin/cupsd"
Nov 22 07:56:08 adam-desktop kernel: [80836.263200] type=1503 audit(1227365768.6
70:15): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsui
d=7 name="/var/run/samba/gencache.tdb" pid=20985 profile="/usr/sbin/cupsd"
Nov 22 07:56:10 adam-desktop kernel: [80838.026641] type=1503 audit(1227365770.4
34:16): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fs
uid=7 name="/dev/tty" pid=21026 profile="/usr/sbin/cupsd"
Nov 22 08:01:48 adam-desktop kernel: [81175.683477] cdrom: This disc doesn't hav
e any tracks I recognize!
Nov 22 08:19:45 adam-desktop kernel: [82253.345471] UDF-fs: No VRS found
Nov 22 08:21:05 adam-desktop kernel: [82333.367443] UDF-fs: No VRS found


```

---

### Post by AdamGott on 2008-11-22
It also appears that my USB devices no longer auto mount.  All devices/media show up If I go to the Places/Computer tab in Gnome and I can right click and mount from there.  My Sansa E280 (MP3 player) shows up with the correct name this way but any mounted cd's/dvd's show up as cdrom0.

Any advice?  I have searched the net in vain thus far.

---

