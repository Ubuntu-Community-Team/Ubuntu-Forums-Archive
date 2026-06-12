---
title: "Buffer i/o error on device dm-10"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by helwitch on 2005-09-04
During boot, just after 'Starting enterprise volume management system' I get about an hour and a half of the following error message.
Buffer i/o error on device dm-10 logical block 6******
After 90 minutes or so, the system boots normally and runs just fine. I've yet to be around to see what specifically it says after all those i/o errors, cos I go do other things.
I've tried commenting out all but my / and /home and /swap partitons in fstab, but this still happens! How the heck do I find out what DM-10 is, and make the system quit looking at it on boot? I'm assuming it's a particular drive or partition, because this problem didn't start until I edited fstab to automount some partitions at boot. But commenting out those partitions hasn't solved the problem! Help!

---

### Post by skoal on 2005-09-04
> "Buffer i/o error"

You're about to lose your drive.  I would suggest backing up important information as soon as you can.

\\//_

---

### Post by helwitch on 2005-09-06
[QUOTE=skoal]> "Buffer i/o error"

You're about to lose your drive.  I would suggest backing up important information as soon as you can.

\\//_[/QUOTE]
WHICH drive? There's 7 of them!

---

### Post by nadamsieee on 2006-10-23
You probably just need to disable RAID:

[http://www.ubuntuforums.org/showthread.php?t=276930](http://www.ubuntuforums.org/showthread.php?t=276930)

The "dm-10" stuff is from dmraid (Device Mapper RAID), I think:

[http://people.redhat.com/~heinzm/sw/dmraid/readme](http://people.redhat.com/~heinzm/sw/dmraid/readme)
[http://linux-ata.org/faq-sata-raid.html#dmraid](http://linux-ata.org/faq-sata-raid.html#dmraid)

---

