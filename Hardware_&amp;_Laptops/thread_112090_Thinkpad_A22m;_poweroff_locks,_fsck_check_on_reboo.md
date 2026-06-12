---
title: "Thinkpad A22m; poweroff locks, fsck check on reboot... GAH!"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by Digimer on 2006-01-03
Hi all,

  I recently migrated to Ubuntu from Debian looking for better media support, which I found and love. 

However...

  Whenever I reboot the systems stops when trying to shut down a SQL server (both mysql and postgres). If I manually shut down the sql server first though, it shuts down fine. 

  Regardless of how I shut down though, on reboot the system complains that the hard drive has problems and runs 'fsck' and, over half the time, drops me to a single user shell and tells me to manually run 'fsck'. It always finds several problems which it fixes but this has already cost me valuable data (though I had a backup so it was easy enough to recover, but still...).

  To rule out problems I used memtest to fully check out my RAM and I ran all the SeaTools (Seagate) hard drive diagnostics and everything hardware wise came up fine, so I am pretty sure this is an Ubuntu problem... :confused: 

  I am not so sure if this is a laptop problem though, so if I should ask this question in another forum please either (mods) move this thread or let me know and I will ask it again elsewhere.

  Thanks all!

Madison

PS - If any logs/diagnostic output would help, just ask...

---

