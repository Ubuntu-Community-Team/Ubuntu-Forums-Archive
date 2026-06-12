---
title: "Mount disk by UUID after filesystem change"
date: 2009-09-06
forum: Hardware
---

### Post by sedd on 2009-09-06
Hi,

This old computer has been repurposed as a media center and where it used to be 80% ubuntu / 20% windows it's now 20% ubuntu / 80% windows (for various hardware and wife related reasons which I won't get into.) I've reformatted the drive with all of our music, photos, etc., from reiserfs to ntfs. The drive mounts fine in both windows and ubuntu, but it no longer shows up in /dev/disk/by-uuid, and so I have to refer to it by the old /dev/sda1 name, which isn't a problem I guess (until I add or remove a drive.) 

What's weird is that blkid shows the same UUID but says that it's still reiserfs. I think this is most likely the problem. Why would blkid still think that it's reiserfs after I've reformatted to ntfs?

---

### Post by Bachstelze on 2009-09-06
How did you reformat? Have you rebooted since then?

---

### Post by Lampi on 2009-09-06
try ls -l /dev/disk/by-uuid/ and check for hdxx entries - I know they are supposed to be sdxx but this is NTFS, so - there is a possible mixup in drive enumeration.

You can also check the gnome device manager - have a look at [this Screenshot]("http://img507.imageshack.us/img507/3135/haldevicemanagertb3.jpg") to show you how

---

