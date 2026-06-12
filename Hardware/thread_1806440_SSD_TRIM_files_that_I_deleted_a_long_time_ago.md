---
title: "SSD TRIM files that I deleted a long time ago"
date: 2011-07-17
forum: Hardware
---

### Post by chrisstankevitz on 2011-07-17
Hi,

ubuntu 10.10

I have an SSD and ext4 and I have not added "discard" to my fstab.  This means the files I have been deleting for the past 6 months have not been TRIM-ed.

I just added "discard" to my fstab, so in the future when I delete files, they will be TRIM-ed.

Question: How do I TRIM the gigabytes of files I deleted over the past 6 months when TRIM/discard was not enabled?

Thank you,

Chris

---

### Post by chrisstankevitz on 2011-07-21
Apparent answer: fstrim

[http://manpages.ubuntu.com/manpages/oneiric/man8/fstrim.8.html]("http://manpages.ubuntu.com/manpages/oneiric/man8/fstrim.8.html")

Not available in 10.10.

Chris

---

