---
title: "SoftRAID problem after removing device"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by countryboy on 2006-04-05
Hello

I installed uBuntu with the following configuration:

3 160gig SATA drives

1 x RAID 1 group across all 3 drives for the /boot (100mb)
1 x RAID 5 group across all 3 drives from the / (remaining disk space)

It all works fine, including when I removed one of the disks and rebooted.

but when I put the disk back in the server it says:

"Starting Enterprise Volume Managment System"
*** glibc detected *** corrupted double-linked list: 0x08066500 ***

and the it just sits there, forever.

If I remove the disk that I had previously removed, then it boots up again without a problem. Put it back in and the error returns.

Any help appreciated

---

