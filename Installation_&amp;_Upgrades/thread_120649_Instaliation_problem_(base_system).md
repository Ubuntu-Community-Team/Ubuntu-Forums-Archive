---
title: "Instaliation problem (base system)"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by Liolikas on 2006-01-23
I have error:
"Unable to instal initrd-tools"
In intaliation step "instaling base system" at ~60%.
Can someone help? [-o<

---

### Post by Luke771 on 2006-01-23
Did it take a long time installing the base system before getting to 60% and to the the error?
maybe hanging on 6% for a (long) while?

---

### Post by Liolikas on 2006-01-23
Yes it hangs at 6% and at 48% little longer than on other percents.

---

### Post by Luke771 on 2006-01-23
I had the same problem, it is caused by a bad hard drive; replace it and all will go fine.
Before you do that, just to be sure, you could boot from a Live cd and run ```

grep hd /var/log/messages

```
If you get many errors, then your problem is actually the hard drive.
I added another drive, kept Windows on the bad one and installed Ubuntu on the new one; it works fine, except som esmall problems when mounting windows partitions from /etc/fstab, but that's not a real problem (not for me anyways)

---

### Post by Liolikas on 2006-01-23
Oh, my harddrive wonking nice with windoze. :confused: but I'll test it.

And THX for help.

---

### Post by Luke771 on 2006-01-23
I got the same problem.
The drive worked nice under WinXP but it was not good enough to run Linux on it, so I added a new drive and installed Ubuntu on it, keeping Win on the old one , and all went smoothly.

---

