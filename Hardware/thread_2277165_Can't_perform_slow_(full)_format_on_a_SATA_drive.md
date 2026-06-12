---
title: "Can't perform slow (full) format on a SATA drive"
date: 2015-05-07
forum: Hardware
---

### Post by AliPM on 2015-05-07
Hi,

I have an old SATA I drive which I am selling, so I want to fully format it and erase all data. When I try to do this in Disks, I get the error:

"Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)"

I have deleted the partition that contained all my data in gparted, so the disk is formatted, but the process only took a few seconds so I assume it was just a quick format.

Can anyone advise me how I can force a full format? Thanks in advance

---

### Post by dino99 on 2015-05-07
Go to your SSD manufacturer's website and they should have a toolbox or utility that will secure erase your drive. 

removing partition, quick erase, does not remove your data; it simply allow to overwrite them. That is why recovery data/partition can be done (if no new data have been writen).
That said you need to do a secure erase, or fully write that ssd with 0 (or else) multiple times (> 7)
[http://superuser.com/questions/101465/how-can-i-securely-format-a-solid-state-drive](http://superuser.com/questions/101465/how-can-i-securely-format-a-solid-state-drive)

---

### Post by SeijiSensei on 2015-05-07
You could also try something like this: [http://download.cnet.com/BCWipe-for-Linux/3000-2144_4-75305695.html](http://download.cnet.com/BCWipe-for-Linux/3000-2144_4-75305695.html)

---

