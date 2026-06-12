---
title: "Strange Automounting Problem"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by makisupa123 on 2005-06-27
A few weeks ago i got a new DVD/CD burner for my laptop.  I slid it in the slot and made the appropriate line in fstab and "viola!" -- it worked like a charm.  But this drive was slightly defective (it didn't open correctly -- a physical problem with the mechanism) so i replaced it with the same model drive (or so i think).  Now, the drive wont automount any media.  It works fine, plays cds, DVDs, and burns CDs but I have to mount it by hand.  My other CD drive and removable media still automount fine.  Any ideas?  Any ideas where i should start looking?


Thanks,

Mak.

---

### Post by argux on 2005-06-28
Hi, I hope to be of some help here,

sounds like whatever is doing the automounting identifies the drives by a unique id number. I don't remember much about that. If you need a pointer on where to start looking, you can read some udev documentation, thought It might not help you with your problem. 

[http://www.reactivated.net/udevrules.php](http://www.reactivated.net/udevrules.php) and 
[http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html](http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html)

Or maybe if you find out what program handles automounting, and where its configuration file is, you might try to reconfigure it. 

(Also, have you checked the Removable Drives and Media entry on the System>Preferences menu? Maybe the setting got modified for some reason)

Hope this helps,
Cheers!

---

