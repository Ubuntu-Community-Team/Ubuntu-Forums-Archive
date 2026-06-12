---
title: "Ext. hdd volume changing device location"
date: 2011-07-12
forum: Hardware
---

### Post by jdavis72 on 2011-07-12
I have a Seagate FreeAgent desktop 2TB usb external hdd on Ubuntu 10.10, with the full drive encrypted with Truecrypt. When I plug the drive in, I can decrypt it with Truecrypt just fine, and can read and write the files too. But after a while, the drive goes into its spin down mode and when I go to select it, the mount point is empty. The volume location has changed. For instance, when I first mount it, say it's volume is at /dev/sdc. After its power down period, I then go to the same mount point that's now empty, and it's volume location has changed to /dev/sdi. I have two other different drives formated the same way that do not change their volume locations on their own. I can unmount it in Truecrypt, then select the drive's new volume location and remount fine. But I can't have an automatic backup with it doing this. Is this a drive issue, Ubuntu issue, or a Truecrypt issue? I have tried changing the usb ports around with no luck. The truecrypt volume is formated as ext4. I formated it out of the box with truecrypt so I don't know if it did this before Truecrypt. Thanks in advance!

Jeremy

---

### Post by jdavis72 on 2011-07-19
Does anybody have an idea?

---

### Post by psusi on 2011-07-19
It is a broken drive issue; drives are not supposed to just power down and disconnect from the bus on their own.  Contact the manufacturer and ask if there is a way to turn this "feature" off.

---

