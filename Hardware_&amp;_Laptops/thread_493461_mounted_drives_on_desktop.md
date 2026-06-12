---
title: "mounted drives on desktop?"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by isecore on 2007-07-05
Quick question, am I barking up the wrong tree when I expect harddrives to show up on my desktop after mounting them in /media/somedrive?

Because earlier today I got tired of having Windows installed. 100+ gigs of crap that I haven't used in 6 months. Old games, programs, etc - all that crap was just filling up my two other drives (S-ATA, one 120 gigger and one 200 gigger).

So first I moved whatever stuff I wanted to keep to other drives and other computers, and after that it was just a few minutes of commands in the terminal and they'd been repartitioned to EXT3. After that I made two dirs in /media - one called 120gig and one called 200gig, and mounted respective drive in respective directory.

But they don't show up on the desktop or in the Places-menu. Is this normal behavior or is something amiss? I don't really mind either way, but it would be nice if they showed up at least in the Places-menu.

Thanks for any input.

EDIT: Here's the /etc/fstab entries relevant to the drives in case anyone is curious.
```

/dev/sda1 /media/120gig ext3 defaults,errors=remount-ro,users,user_xattr,user 0  0  
/dev/sdb1 /media/200gig ext3 defaults,errors=remount-ro,users,user_xattr,user 0  0  
```

EDIT2: I should've just rebooted immedately. The "problem" resolved itself then. Silly me! I'm just so darn used to not having to reboot.

---

