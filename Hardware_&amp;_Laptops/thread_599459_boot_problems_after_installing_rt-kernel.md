---
title: "boot problems after installing rt-kernel"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by leader303 on 2007-11-01
as the header says: i installed the rt-kernel (2.6.22) for my ubuntu studio and now have some problems with booting. rt won't boot at all, just gives me the flashing cursor and an impressive fan noise due to heating up, lowlatency boots but has no sound (maybe because it's still 2.6.20? but that's another topic, haven't really tried it there...), and generic (2.6.22) boots about one out of three times. the other two times the progress bar is stuck at about 70%.
any ideas what i could do about that? how can i display the system messages instead of that image?

---

### Post by ROBarber on 2007-11-02
it seems that you have some harddrive problems. you should scan it using fsck at boot start or using this

[http://ubuntuforums.org/showthread.php?t=295262]("http://ubuntuforums.org/showthread.php?t=295262")

good luck

---

### Post by leader303 on 2007-11-25
well. fsck'ed the hd, no problems found, rt still won't boot.
is there anything else i should have apt-got except for linux-rt and linux-headers-rt (whatever that is)?

---

### Post by terrax on 2007-11-28
I can't boot the linux-rt kernel either.
It just freeze at early stages at boot.

I can't even give you a log file, because it freeze so early that the harddisk almost hasn't started yet. Any got any ideas?

---

### Post by leader303 on 2007-12-03
erm, bump?

---

### Post by dcstar on 2007-12-15
> **leader303 said:**
> erm, bump?

I've now given up on the Ubuntu rt kernel, about one in every 5 boots it doesn't initialise my Nvidia video hardware and just hangs after the initial splash screen.

The generic kernel does not seem to have this problem, and if I get motivated I'll (again) create my own kernel with the "CK" enhancements.

---

### Post by ankara on 2007-12-21
i never found the video driver problems when uing ubuntu studio RT kernel on edgy eft 7.04.
strange that with both ATI (PCIe) and Nvidia (onboard gpu) the video drivers fail to load. 
FYI there is a thread [here](http://ubuntuforums.org/showthread.php?p=3793427#post3793427) regarding recompiling your kernel with the paravirtalisation option turned off although this does seem to lead to new problems and a possible (unconfirmed) violation of the GPL. despite this caveat, the fix does work, ive tried it.
hth

---

### Post by ankara on 2007-12-21
@ Leader303
use the recovery version of the RT kernel at the grub boot screen to show all the info.
to view the dmesg output from boot, use ```
dmesg | tail
```you can also use ```
dmesg > dmesg.txt
``` to output the text to a file for later viewing

---

