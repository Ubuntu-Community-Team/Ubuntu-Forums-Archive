---
title: "Issue with Gparted resizing XFS partition."
date: 2008-10-04
forum: General Help
---

### Post by djbon2112 on 2008-10-04
I have a RAID array with a total size of 2.73 TiB. I currently have an XFS partition on it of 2.05 TiB. I'm trying to grow the partition to the full size of the RAID using Gparted, but I get the following error:

"a partition with used sectors <x> greater than its length <y> is not valid"

...where x and y are some really big numbers. I'd try something else but Gparted seems to be the only program with good XFS support. If anyone's seen this problem before, I'd appreciate any help!

---

### Post by Sef on 2008-10-04
You need to find out if there is [kernel support]("http://gparted.sourceforge.net/features.php") for it first.

---

### Post by djbon2112 on 2008-10-04
There is kernel support. I loaded it with "modprobe xfs", and I had to do this before I even got to this step. This happens after I resize it, then press "OK".

---

### Post by fjgaude on 2008-10-05
Might be time to file a bug report... these large drives haven't been around very long and likely many programs haven't been altered to handle them correctly.

In fact GParted just stated handling xfs recently.

---

### Post by djbon2112 on 2008-10-05
> **fjgaude said:**
> Might be time to file a bug report... these large drives haven't been around very long and likely many programs haven't been altered to handle them correctly.

In fact GParted just stated handling xfs recently.

Alright, thanks for the info! I figured I'd ask before filing a report.

---

