---
title: "Floppy drive: Not mounting"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by godwinoganiru on 2006-12-16
Since I istalled Ubuntu I have never been able to mount or access my floppy drive. I tried disk mounter but each time I get the error message below:

"given UDI is not a mountable drive"

I also tried formatting the floppy, purchasing a new floppy disk, but still didn't solve the problem. Any help please?

---

### Post by Oceola on 2006-12-27
I have the same problem.
I found one solution which suggests updating the pmount to 9.6-1 from the Dapper repository. This for a Breezy solution and the second possible solution was to place hal with the floppy group.
I've tried neither as of yet. My floppy works fine in my Compaq with their stock floppy hardware and was picked up in both Hoary and Breezy on the Compaq but the floppy in the Gateway doesn't allow it to mount, same comment. I can format using gFloppy, which makes no sense if it can format why can't it mount. Device manager shows pretty much the same info for both except Gateway floppy is PnP0600 and the Compaq is PnP0600

I found some flash drives which seem to work and will be using them until I can get the floppy working for simple file transfers.

Good Luck

---

