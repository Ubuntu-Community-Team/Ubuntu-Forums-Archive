---
title: "Harddrive spindown not working optimaly"
date: 2008-11-20
forum: Hardware
---

### Post by mkoonstra on 2008-11-20
I am trying to acchieve that a disc that is holding data is stopped after 15m of inactivity (note that the os is on another disc. Now I have found this to be possible with:

sudo hdparm -S 180 /dev/sda

However, this is working one time only, after beeing woken up later, it seems to forget this setting and forget to spin down again. The only thing that works in this case is reissueing the command to enable it again, and then, it will spin down after 15 minutes.

Note that no partitions on this disc are mounted during testing, so no activity should be there.

I have tried this with another (Maxtor) disc which does exactly what it should do.

I am using a Samsung Spinpoint F1 750gb.

---

