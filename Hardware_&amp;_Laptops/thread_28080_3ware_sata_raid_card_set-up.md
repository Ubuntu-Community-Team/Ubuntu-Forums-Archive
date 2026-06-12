---
title: "3ware sata raid card set-up"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by martinez9049 on 2005-04-18
hi, i have a 3ware sata raid card with currently only one hd on it. how do i get linux to detect it or set it up? this is not my primary hd. right now im not interested in running an array, i just want access to the disk

thanks.
ismael m

---

### Post by alastair on 2005-04-18
I don't own one, and have never used one - but don't 3Ware have a BIOS utility to control attached devices? I thought they were just presented as a SCSI device?

At boot up, you should see what the kernel thinks it has attached (/var/log/syslog).

---

### Post by martinez9049 on 2005-04-18
it does have a bios utility...and it's seeing the hard drive. is it just a matter of mounting it in ubuntu? im new to linux so im not sure how all this stuff goes.

thanks,
ismael m

---

