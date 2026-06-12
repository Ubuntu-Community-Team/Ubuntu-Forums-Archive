---
title: "New HD; Can Someone Check my Plan?"
date: 2008-09-10
forum: General Help
---

### Post by strange_cathect on 2008-09-10
Hello, would a few experts mind telling me if this plan will work, or what problems I will encounter? 

Basically, I need to install a new HD. But I want to save my old /home data and transfer it to the new HD.

My idea:

> **STEP ONE**:

Put the new HD in my external enclosure. Format 3 partitions for use as /, /home, and /swap.

**STEP TWO:**
RSYNC the old /home data over to the new drive partition that will become the new /home.

**STEP THREE:**

Remove the new drive from the enclosure, install in the machine, and boot using the Live CD.

**STEP FOUR:**

Go through installation, pointing the installer to the partitions for / and /swap, but tell the installer not to format my /home.


Will I have any difficulty with permissions for /home? Any problems with this?

Thanks for your help in advance!

---

### Post by ad_267 on 2008-09-10
I think if you recursively chown the home drive once you install then you should be ok (sudo chown -R username username /home/username). There could be issues with configuration files if you are using a different version of Ubuntu or another distribution.

---

### Post by HermanAB on 2008-09-10
The usual way to do this is to boot off a live CD (Knoppix) with both disks plugged in.  Then use dd to copy from the old to the new disk.  Thereafter use gparted to enlarge the partition to fill the new disk.  Finally, install the new disk and reboot.

Hope that helps!

Herman

---

### Post by -Zeus- on 2008-09-10
why would he use knoppix?

---

### Post by werries on 2008-09-10
you can just use dd on ubuntu instead of knoppix. DD would work best, you just keep your entire installation. :)

---

### Post by strange_cathect on 2008-09-10
I want to do a fresh install of /. I don't know what DD is.

---

