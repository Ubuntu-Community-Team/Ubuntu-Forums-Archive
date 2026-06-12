---
title: "&quot;Invalid mount option when attemptiong to mount the volume 'My Disc'"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-07-06
I have a data DVD that I burned a few months ago.  When I try to put it in my Ubuntu laptop, I get an error box that says "Cannot mount volume. Invalid mount option when attemptiong to mount the volume 'My Disc'"

Any ideas?

---

### Post by geraldm on 2007-07-06
It would help to post the command used, so that the invalid option could be 
seen by all;  if the command defaulted to options in file /etc/fstab, then also
posting that line for the device used.
man mount # check this manpage.  The options within are shown by filesystem 
type, so you need to know what filesystem is on the DVD, which would probably
be UDF, or iso9660 for CD disk.

Gerald

---

### Post by diablo75 on 2007-07-06
I never entered a command.  I simply placed a DVD in the drive tray, pushed it in, and up comes the error.

However, oddly enough, VMware installed on the same PC (with Windows XP installed in it) opens the same disk with no problem.

Other DVD's that were burnt along side this disc can be accessed by Ubuntu without a problem.

---

### Post by geraldm on 2007-07-07
In that case, the error message is started from the options listed in
the line in the file /etc/fstab.  Somehow, the disk inserted is different
or unrecognizable compared to the options specified. 
Geald

---

### Post by juan2202 on 2007-07-08
I am having this issue when using a data DVD.  Has anyone found a solution?

I tried [this]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233") but I still get the same errors :(

---

