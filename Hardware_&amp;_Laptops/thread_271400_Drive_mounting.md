---
title: "Drive mounting?"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by darundal on 2006-10-04
Ok, I recently reformatted one of my Hard Drives as ext3. It doesn't have an fstab entry, and it may or may not mount automatically (generally to /tmp/disks-conf-sdc1, although if I tell it to mount to a different location in the disk manager it will use that location for a little while...). Also, it actually detects it twice in the disk manager: first, an entry at the top showing it with the icon used for USB Disks, and then again at the bottom of the list before the CD/DVD drives and my floppy drive. The first one shows as having no partitions, and shows no information for it other than that. It doesn't state a device. The second one shows up just like any other disk in my system. The device shows up as /dev/sdc, and it properly shows how much is used. I tried to add an fstab entry for it so it would mount automatically at boot, but the fstab entry had absolutly no effect whatsoever. Also (probably) relevent is that since having formatted this drive, my computer won't recognize external hard drives over USB. I am totally lost. HELP!

---

