---
title: "Laptop Freezes When Removed from AC"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by willfe on 2006-09-06
Greetings, all! I've been running Dapper Drake without incident on this notebook for quite awhile (including before release; it was remarkably stable on this box), but for a couple of weeks now at least, if I unplug the notebook from A/C (with a fully-charged battery), the machine instantly freezes. Amusingly, the computer will cheerfully remain powered by the battery for a couple hours just displaying the frozen environment if you let it just sit there :)

I've tried booting the kernel with noapic and noacpi options, and all combinations of these (both, one or the other, and neither) make no difference whatsoever.

The machine is an HP Pavilion ze2000 (the el-cheapo one Walmart was selling way back in 2005 on "Black Friday" for $379); it's been a rock-solid machine until now.

```

$ uname -a
Linux bacchus 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686 GNU/Linux
```

Not sure what other debugging info to include, so feel free to thwack me with the clue-by-four if needed. Any input on how to solve this would be much appreciated; I use this machine for production shows on occasion and it'd be handy to just leave it running when I move around instead of having to reboot when I get to a gig.

Thanks!

---

### Post by spier on 2006-09-06
Seems there are some issues related to the way Power management (PM) read battery status. Maybe disabling PM actions while on battery?

---

