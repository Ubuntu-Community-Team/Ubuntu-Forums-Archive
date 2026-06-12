---
title: "mdadm: md device /dev/md0 does not appear to be active"
date: 2017-08-04
forum: Hardware
---

### Post by lakitu2 on 2017-08-04
hey - here's a quick run-down:

<lakitu>30 hey - i'm inbetween places i want to with my RAID array. wondering if someone knowledgeable can hold my hand thru it
20<lakitu>30 i have a 2-device RAID1. one of the disks became unplugged while it was off, & according to what i read, i should try --re-add or --add, depending on the event count. i tried --re-add, but only --add would take
20<lakitu>30 that completed (--add the harddrive that became disconnected to the array) after a long process
20<lakitu>30 when that completed, i restarted & now it says "mdadm: md device /dev/md0 does not appear to be active" when i do sudo mdadm --detail /dev/md0
20<lakitu>30 sudo mdadm --examine /dev/sd[ab] both return listings (e.g. /dev/sda: MBR Magic: aa55; Partition [0] : 40938240932 sectors at 1 (type ee)"
20<lakitu>30 err ")"
20<lakitu>30 wondering if the next step is --assemble, or what

any helpful info can be provided. mid-level linux user.

thanks!

---

### Post by oldos2er on 2017-08-04
Ubuntu version?

---

### Post by lakitu2 on 2017-08-04
thanks so much for fast response, but I rebooted again, & checked connections. I'm not sure if i'm having problems with PCI card's SATA ports, or what, but it was all working when i got back in. will check back if more problems. phew!

joe

---

### Post by oldos2er on 2017-08-04
That doesn't answer the question?

---

