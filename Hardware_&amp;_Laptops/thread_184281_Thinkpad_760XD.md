---
title: "Thinkpad 760XD"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by n2diy on 2006-05-29
I've been using Breezy for a month now, and would like to install it on my ancient laptop.

The laptop won't boot from the cd-rom, and the cd-rom has to be removed from the system, to install the floppy drive.

Currently the laptop is running FC1, and I can see the data on the Ubuntu cd, is there a file I can execute to start the Ubuntu install?

TIA

Darryl

---

### Post by rudyard on 2006-05-30
Hi NT,
founf it hard to believe you can't bot from CD so I Googled it. Whoa! You can't! Sux! Anyway, I found this
[http://www.stephanmaus.de/netbsd-on-thinkpad-760-xl.htm](http://www.stephanmaus.de/netbsd-on-thinkpad-760-xl.htm)
and this makes me wonder if you can partition your drive and drop the files from the CD there and boot from the floppy. Folks here are super helpful; sorry, don't have more for you, I've used Linux for about 5 days.
-Rudyard

---

### Post by n2diy on 2006-05-30
[QUOTE=rudyard]Hi NT,
founf it hard to believe you can't bot from CD so I Googled it. Whoa! You can't! Sux! Anyway, I found this
[http://www.stephanmaus.de/netbsd-on-thinkpad-760-xl.htm](http://www.stephanmaus.de/netbsd-on-thinkpad-760-xl.htm)
and this makes me wonder if you can partition your drive and drop the files from the CD there and boot from the floppy. Folks here are super helpful; sorry, don't have more for you, I've used Linux for about 5 days.
-Rudyard[/QUOTE]
Thanks for the advice.

If I was able to do that, I'd still need to know which file on the cd starts the install, and the install is going to let me repartition the drive, so I don't see any advantage to wiping out the current partition?

So, I'm back to the original question, which file on the cd starts the install process?

TIA

Darryl

---

### Post by electrofox on 2007-12-05
Try typing "server"  at the ubuntu boot prompt ("boot: "), I think.
Hope that helps.  (Especially since someone might be giving me the same computer soon, and I plan on doing the same.  Would you let me know if it works?)
Best,
-ElectroFox

---

### Post by ozzymud on 2008-01-05
Just surfing around about an old 760XL im playing with, thought i might post something i found that helped me a ton.

Smart Boot Manager: [http://paulski.com/zpages.php?id=1612](http://paulski.com/zpages.php?id=1612)

get the zipped image, use rawrite under windows or
# dd if=image of=/dev/fd0          (where image is the image filename)
# cmp image /dev/fd0               (where image is the image filename)
in linux... boot from the floppy... choose the install option to HD0

reboot sans floppy with cd installed, rescan bootalble devices... your CD will no show up and you can boot from it.

This 760 has 40mb ram and im on hour 5 of waiting for fluxbuntu to finish installing.

using the guide at [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)
(Note: Set of characters that should be supported by the console font:  <-- latin1 for English)

Hope this helps someone looking for info :)
Ozzy

---

